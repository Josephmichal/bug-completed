# HTTP PROTOCOL & HEADERS
-->In simple words, a web server serves HTTP requests
-->when a browser requests a file over http protocol the web server accepts the requests, find the requested document and sends back to the browser
-->rand aalukal thamil communicate chyanamengil randperkum ariyavuna oru language samsarikanam.athupole browser um server um thamil communicate chyan HTTP protocol use chyunu.
-->==NOTE:server ennath oru computer aan.aa comiputer il aan nammude applications um mattu karyanglum okke save aayi kidakunath.so namal oru file request kodukumbol namude request ee server enna computer ilek pokunu enit aa computer il aa sathanam undnegil aa computer namuk ath tharunu ok==
-->Wireshark tool use chyth namuk traffic oke nokam apol ellam manasilakum
-->GET request il Range: bytes=0-1024  enna header koduthal aa request il ulla athrem bytes mathram namuk response aayi kitum.ithinte partial GET request enn parayum.ee reethi namuk chyanengil HTTP/1.1 protocol aayirikanam use chyunath.vere aanengil ith work aakila.ith vech namuk videos oke korach mathramayi retrieve chyam
-->partial GET request il namuk 200 ok response alla marich 206 response aan status il varuka
-->namal oru file download chyukayanengil edak vech ath nin poyal chelapo aa file download chyan adyam muthale chyendi varum.athin pakaram ee reethi server use chyum apol pakuthik vech resume chyan patum
-->POST is used to send some data to the server to be processed in some way eg: login pages
-->Cache-Control: public   ennal aa response il ulla body publick proxy server mathrame cache chyan patu allathe private proxy servers in patilla.private proxy server ennal browsers aan
-->Debugging related purpuses inan TRACE header use chyar
-->athayath namal oru request ayakumbol pala proxies vazhi aan aa request server il ethunath. ivan kanikumbol rand cache proxies vazhiyan server il ethunath.so namuk areela ee proxy vazhi namude request kadanupokumbol request in enthoke matangal aan varunathen.so namal 
TRACE / ... enn request ayakumbol server aa same request thane namuk response aayi tharum apol namuk ariyam request il enthoke nadanu enn.
-->ivan ith kanikanayi burpsuite load chyunu enit curl upayogich TRACE vech send chyunu enit burp il intercept chyth puthiya oru header kodukunu enit forward chyunu.ini terminalil response varum apol ee puthiya header um response il kanan patum -> `curl -X "TRACE" --proxy 127.0.0.1:8080 example.com`  
-->so ingane namuk browser intem server intem idakula proxies il enthoke nadakunu enn manasilakam 
-->in real world TRACE header is disabled in nginx servers
-->OPTIONS enna method use chyunathenthinanenal oru request il ethoke methods use chyan patum enn ariyan aan.chela request il GET method use chyan patila especially login pages oke athikam POST methods aayirikum.so ath ariya OPTIONS method use chyam
-->ngins servers il OPTIONS method disabled aan.but apache server il OPTIONS method use chyan patum

==========================================================

# Getting started with nginx
-->apache files oke /etc/httpd directory il aan undavuka
-->nginx files oke /etc/nginx directory il aan undavuka athil thane nginx.conf enna file undakum ath important aan.so nano nginx.conf  adich athil oro karyangal nokuka
-->nginx il master process undakum athupole worker process undakum.master process aan worker process undakuka.worker process aan clients inte oro request oke handle chyuka. athayath clients(browser) worker process umayan interact chyuka.ethra servers venam ennoke master class theerumanikum.
-->so adyam kanuna user nginx ennath master process aan.ps vech nokiyal namuk kanan patum. athinushesham ullathan ethram worker process venam ennulla code.athinu shesham ithil kanuna pid ennath master process inte process id aan
-->nginx -t  enn terminalil adichal ngins.conf il enthelum problems undengil ath manasilakan patum
-->mainly 5 MIME types aan ullath 
- application/
- audio/
- image/
- text/
- video/

ithil adyatheth type um slash in shesham varunath subtype um aan.ie, application/pdf, application/zip ... image/jpeg,image/png

==============================================================

# Reverse Proxy
-->generally between the web browser and the application server sits the nginx  
`browser<->nginx<->application` 
ie, CLIENT (google.com)  <--> PROXY (192.168.12.48)  <--> WEB SERVER (192.168.12.49)
so client webserverumayi nerit interact chyunila proxy server umayi mathram aan.so namal terminalil ping google.com ennoke adikumbol aa application inte r.proxy inte ip aayirikam kitunath areela.NOTE:- namal nginx server linux il install chyanam enit linux il nginx il route oke koduth aan path oke chyunath.ellam namal thane aan chyunath allathe namal host chyth kazhinj nginx swayam chyunathala nginx inte code um namal thane aan chyunath.
-->so browser oru page request chyumbol aa request aadyam nginx reverse proxy ilek pokum avide ninn application server ilek pokunu.enit application response nere nginx reverse proxy lek ayakunu.avide ninum nginx browser ilek aa response ayakunu.athayath browser intem appliation te naduvilayi nginx nilkunu
-->ingane nginx middle aayi nilkunathinte reverse proxy ennu parayunu
-->ithukond thane browser in backendumayi communicate chyenda avstha varunila pakaram nginx aa work chutholum.browser nginx umayi mathrame communicate chyunulu
-->application server ennal otta orennam alla.kore servers undakum.namuk venda page/path eth server il aano ullath angotek ee reverse proxy request ayakum.media server,gaming server, application server etc.namuk pictures aan vendathengilum ath chelapo media server il aaayirikum undavuka apol namude request aa serverilek pokum enit avide ninum response varum
-->so reverse proxy vazhi aano request vanath enn engane aryam enn ivide ivan example aayi kanikunund.athyath rand terminal edukunu.onu reverse proxy randamatheth backend app aan.so ivan browser il aa backend pathilek search chyunu.so enit proxy ulla terminalil nokumbol namude request kanikunund.athupole backend app inte terminal nokumbol avidem aa request kanikunund.avide nokumbol namuk kanam evide ninuman request vanathen ==apol namuk kanam oru ip adress = 192.168.189.140 . ith namude ip alla pakaram nginx reverse proxy ide ip address aan(ifconfig adkumbol kanam).so angane namuk manasilakam ee request vanath reverse proxy il ninumanen==

### Understanding proxy_pass directive :
-->proxy pass directive forward the request to the proxied servers specified along with this directive.athayath namal ayakuna request eth serverilek pokanam enoke configure chyunath ee proxy_pass vazhiyan
-->simple example :
            location / {
	            proxy_pass http://192.168.10.50;
	            }

so namal /  enna pathilek request ayakumbol ath reverse proxy vazhi ee 192.168.10.50 enna ip lekan pokunath.ee ip ennath server aan.njan paranju kore server undakumen.so athil etho oru server inte ip aan ee ip.ingane namuk oru reverse proxy undakam patum
-->ithupole location /admin, location /app   angane oro path inum namuk route chyan patum. apol varuna request in anusarich angot poi kolum.admin thane ayyi oru server undayekam
-->namuk nere backend application ilekan pokendath pakshe reverse proxy ilude pokan patu. ennumvech reverse proxy undengile namuk venda page kitu enonum ila.namuk aa backend application server inte ip ariyamengil direct browser il aa ip koduthal namuk nere application ilek keram.apol reverse proxy ide avisham varunila.ith oru vulnerability test pole nokuka ok

### X-Real-IP
-->nerthe paranju namal oru request ayakumbol proxy vazhi athu poi backend application server il ethumen.apol reverse proxy ide ip aan kanikukua.but real world il eth client il ninano request vanath aa client inte ip aan backend application il kanikendath eg :
location / {
	    proxy_pass http://192.168.10.50;
	    proxy_set_header X-Real-IP $remote_addr;
 }
ivide $remoet_addr ennath oru variable aan.ith kodukumbol request ayacha client inte ip avide varum
-->ini namal page refresh chyumbol namude ip backend application inte access.log file il kanan patum.athupole reverse proxy de ip yum kanan patum
-->ith configure chyunath /etc/nginx/nginx.conf enn file il aan.nano adich ee file il keruka enit athil http {}   part il log_format enna variable il namuk changes varuthiyal mathi ie, '$http_x_real_ip'  enn koduthal mathi apol evide aano ee variable value aayi koduthath aa bhagath namude ip adress kanikum
-->karanam kore aalukal ee application use chyunathale apol avarude ip oke arinjirikande athinan ith mainly use chyunathen thonunu.allathe veruthe nginx inte ip log chyth vechit enth karyam

### Proxy Host Header
-->nginx satharana request backend ilek ayakumbol host: header edukila just GET / HTTP/1.1  mathrame backend ilek ayaku
-->oru backend application server undakumbol kozhapamila but onnil kooduthal servers back end il undengil aan prashanam
-->ipol namal ayakuna request host: kp.net ile GET / request aanen vecho but proxy namude host header backend ilek ayakunila.back end il aanengil rand website unden vecho kp.in and kp.net.so host header illathathkondthane backend in areela eth website inte /  aan tharendathen. so backend kp.in il ninum tharum but namuk vendath kp.net il ninumula GET /   ann
-->so nginx host header um backend ilek ayakumbol use chyanam.athinulath configuration file il aakanam
-->proxy_set_header Host $host;    enn koduthal namuk venda webstie um request inte koode proxy ayakum backendilek

==============================================================

# LOAD BALANCERS
-->ivide nginx load balancer aayi act chyunu.so oro request varumbozhum oro server ilek request ayakunu.angane load balance chyunu
-->health_check interval=5 fails=3 passes=2; 
enn .conf file il chealpo kandekam.health check ennal proxy epozhum ariyanam ethoke server aa running il ullath ennale aa server ilek requests ayakan patu.so athinayi oru GET request automatic aayi proxy ayakum check chyan.so interval means oro 5 second ilum oru normal GET request ayakum.apol server down allengil response kitum.fails means adupich 3 pravisham response vanilengil server down aanen proxy theerumanikum.server veenum pazhayath pole running aanen manasilakan aan passes.athayath rand pravisham pazhayath pole 5 sec interval il response kitithodangiyal server running aanen manasilakum apol pinem aa server ilek request ayakum

==============================================================

# The Caching Subsystem
-->  BROWSER - CACHE - SERVER    ivide rand reethiyil caching undakam onn browser il thane cache chyan patum athupole cache oru middle man pole ninum cache chyan patum athyath nginx proxy server pole.athine intermediary proxy enn parayum
-->browser il ulla cache aanengil ath namude browser il mathrame aa resposne store chythitullu pakaram intermediary proxy il aan cache chythitundengil ath mattu baki users inum orupole aan(web cache poisoning ithil aan chyuka)
- Cache-Control: no-store
           means donot store this particular response anywhere.athayath intermediary proxy il aayalum browser cache il aayalum
- Cache-Control: no-cache
			no-cache ennal no-store pole alla pakaram.caching intermediary proxy ilo allengil browser proxy ilo cache chyth vechitundakum.suppose intermediary proxy il cache chythitunden vecho apol client oru request ayakumvol athinulla response ee cache il undakum but aa respone ayakunathin mumb server il poi ath revalidate chyum enite response ayaku.onukoode parayam athayath caching ivide nakanunundakum satharana pole but cache il ninum response ayakunathin mumb serveril poi revalidate chythite response namuk tharu
- Cache-Control: max-age=0 
			ethra seconds aan caching ullath enn kanikunath.ith both client browser cahcing inum intermediary cache proxy kum bhadhakaman.athayath max-age=120 aanengil rand caching systethilum aa time aakumol cache theerum
- Cache-Control: s-max-age=0
			ith intermediary cache proxy kk mathram bhadhakamaya header aan.this is not for the client side caching(browser caching).so ith kandal athinartham caching intermediary proxy il aanenan 
- Pragma: no-cache
			ith namude Cache-Control: no-cache pole thane aan.ith mainly use chyuka HTTP/1.0 based applications ilan

-->caching enthinan use chyunathenal namal oru page request chyth kityen vecho enit namal aa same page pinem pinem refresh chythondirunal oro thavanayum aa request server il poi response tharanam angane epozhum server il poi response tharenda aavisham ila.so athukondan caching enna sathanam introduce chythath ok

### Content Negotiation
-->namal oru site edukunu oru video streaming site.so namal oru video load chyumbol thane namuk oru particular qualityil aayirikum kituka.mobile il aanengil 480p il aayirikum.desktop il aanengil chelapo 720p or 1080p il aayirikum.so namuk venda karyangal therunathine aan content negotiation enn parayunath
-->ith determine chyunath q= parameter vazhiyan eg: `Accept-Language: dn, en-us;q=0.8`
-->so ivide danish (dn) in q illa.so atinartham q=1 ennan.q=1 ennal most preffered ann.so ivide danish bhashayil content server tharum
-->namal oru image edukunu enn vecho apol `Accept: image/png, image/svg+xml, image/*;q=0.8, */*;q=0.5`  so ivide nokiyal kanam png, svg oke q=1 aan.so athil varum.athil namuk data theran patunilengil last kanam `*/*;q=0.5`  enn so eth MIME type ilum namuk sathanam theran thayar aan.

### Cache-Control and Must validate
-->njn paranju Cache-Control: no-cache aanengil athinartham store chyaruth ennala but it is free to store the respone but aa response ayakunathin mumb server il poi onukoode revalidate chythite response ayakan padulu ennan
-->but if revalidate chyan pokumbol server downa aanengil revalidate chyan patila apol aa varuna resposne ine stale enn parayunu apol namuk older response aan varuka.apol angane veruna older version chelapol chela resquests accept chyila apol use chyuna header aan must-validate. 
-->private cache ennal namude browser il ulla cache ie, client side caching.oru user inte browser il mathram store aakuna cache
-->public cache ennal namude intermediary cache proxy.athyath public aayi ella users inum access chyana cache
-->caching header use chyunathin mumb expires: header aan use chythirunath

### Keep-Alive
-->satharana namuk website il ninum enthengilum access chyenengil aadyam oru connection undakanam.namuk ariyam http ennath tcp il aan work chyunath.TCP connection undakan aadyam 3 way hand shake nadakanam enite namuk HTTP protocol il server umayi communicate chyu
-->server il ninum namuk venda sathanam kiti kazhinjal aa connection apol thane close aakum
-->ini veendum namuk serverumayi communicate chyenenngil veendum aadyam 3 way hand shake nadathanam.athayath oro request inum 3 way handshake nadatheetan communcation nadakuka
-->pakshe ipol oru web application browser use chyumbol ore samayam orupad requests server umayi nadathendi varum apol ee oru reethi use chyuka enn dhushkaramayirikum
-->so athinayi namal request il keep-alive header use chyunu.apol oru tcp connection vech multiple request angot ayakunu athupole multiple response namuk kitunu.so otta tcp connection il thane namuk serverin kore requests ayakam

### Cache Hit & Miss
-->namal oru request ayakumbol athinulla resposne intermediary cache il undengil avide ninum namuk response kitunu.so athan cache HIT
-->athe samayam namuk venda request cache il illengil namude request aa intermediary cache proxy nere server il ayakunu.enit server namuk response tharunu.so athan cache MISS.enit ee varuna response athinte configuration anusarich cache il store chyum or chyilayirikum

### Static Asset
-->satharan namal ipo /index.html file request chyukayanengil aa request reverse proxy vazhi back end server ilek pokum.but index.html retrive chyumbol athinte koode vere files undakum like images.css.javascript file oke undakum.apol aa oro files um ee /index.html enna request vazhi tharanam.ipo 7 extra file koodi undneigl /index.html koodi 8 aakum.apol 8 request backend ilek pokum apol oru 100 per ee same request chythalo kore aakum.apol athinulla pariharaman static aayitulla files oke backend il ninum reverse proxy ilek aakuka.athayath image files css files ...angane ullathoke ini reques varumbol ee reverse proxy(nginx) il ninum namuk kitum athesamayam /index.html um pine athinte koode ulla dynamic files oke aan backend il ninum namuk response aayi varuka apol performance koodum

=======================================================

# Acess Control
### White Listing
-->arkoke mathraman chela pages accessible enn configure chyanth aan nokunath.ivide white list chyth vekum.apol athil ulla ipadress ullavark mathrame access chyan patu
-->eg nokam :
location /admin {
		....
		allow 127.0.0.1;
		deny all;
}

ingnae koduthal ee ip il ulla aaliln mathrame admin page access chyan patu.baki ullathelam deny chyum
-->ivide ipo oru ip ullu.but kore ip undengil oro line ilum allow ip ,allow ip enn kodukathe namuk ee ip s ellam oru whitelist folder il aaki code il include  /etc/nginx/conf.d/whitelist;   enn koduthal mathi
-->base64 encode chyth orikalum username,passwd send chyan padila.pakaram encrypt chyth venam send chyan
### Authentication - Basic
-->Authentication thane 3 type und - basic,digest,NTLM . NTLM angane use chyarilan thonunu.mateth randuman main aayi use chyuka
-->site il http://url/admin  ennadikumbol username,password oke choikum apol namal athinte request nokanam.athik chelapo kanam header -> www-authenticate: Basic realm="family"  enn
-->so namal username,password oke adich send chythal aa send chyuna credentials base64 encode chythan server ilek pokuka.so ath nallathala.athukond basic type authentication nallathala.pakseh basic type authentication aan chyunathengil namuk SSL use chyth chyam.apol credentials encrypted form il aayirikum apol oru hacker in MITM attack chythalum ath decrypt chyan patila
-->ith nginx config file il engnae chyumen nokam :
location /admin {
		....
		auth_basic " Basic Authentication ";             ---1)
		auth_basic_user_file "/etc/nginx/.htpasswd";                    ---2)
}

ithil 1) ennath eth type authentication aan ennathan.ivide basic authentication aan chyunath
ivide 2) ennath user adikuna password eth file il ninum compare chyanam ennathan

### Hashing
-->encryption ennath two way process aan.ie, encrypt chythalum ath namuk key undengil decrytp chyan patum
-->Hashing ennath one way process aan.orikal hash chythal pine ath decrypt chyan patila. decrypt chyan patunilengil pine enthinan use chyunahthen nokam :
1) your system files donot change.namal manually change chyathe namude systethil ulla file change aakila.athava change aayal athile hash comapre chyth ath manasilakum
2) you can store passwords in hashed value instead of encrypted value.passwords hash chythal pine namal ini epol login chyumbozhum namal kodutha password value inte hash value convert chyum enit aa kitiya hash value aano store chythirikua hash value enn confirm chyum.aanengil access kitum 
3) verify the integrity of software that you download.athayath namal microsoft site il ninum oru file download chyunu enn vecho apol aa varuna file in oru hash value undakum. namal aa file download chyunathin idak oru hacker keri vann aa packets inte idayil oru virus ittal ath namuk ariyan patila.apol namal aa file motham dowload chythit hash value compare chyum apol ariyan patum hash value changed aayi enn.ipol ulla ella site um enthengilum download chyumbol hash value tharum

### Authentication - Digest
-->aadyam Digest authentication ulla path ilek pokuka /admin so GET /admin edukuka apol responsil kanam :
HTTP/1.1 401 Authorisation Required
WWW-Authenticate: DIgest realm="Family" nonce=66c3ef...  qop=auth-int

-->so namal username,passwd adich send chyumbol ith md5 hash aayitan pokunath
-->athayath {(username+passwd+realm) = md5 +(path(/admin)+method(GET)) = md5} = md5
-->so ee last vanna md5 Response=md5  enna value aayi serverilek namude username,password ayakunu
-->==Digest Authentication is not supported by NGINX so digest auth use chyenengil apache use chyanam ok==

==========================================================

# Logging Subsystem
-->athayath access.log,error.log files ine patti parayunu.oro user um application il enthoke chythu enn history pole kanikunath

==========================================================

# HTTP Compression
-->namal oru sathanam backend application il ninum edukumbol athinte full ayitulla form il edukunathin pakaram athine compress chythit namal edukunu apol namuk valuthayi bandwidth valikunila
-->oru file 3000 bytes aanengil ath compress oo mato chyth athine cheriya size aaki ayakuna prakriya aan it
-->Accept-Encoding: header use chythan ayakuka(request il aan).ee haeder il mainly moon values aan varuka  ie,  1)gzip  2)deflate  3)compress
-->Accept-Encoding: gzip ennanengil namuk venduka file gzip aayi server borwser ilek ayakum
-->server browser ilek ayakumbol browser ee vannath eth type aanen manasilkan server response il  Content-Encoding: gzip  enn ayakum apol browser in manasilakum ee type il aan content edukendath enn ok
-->pakshe aa response il thane content-type: text/plain   ennum kanam.athayath server ayakuna file compressed aayan ayakunathengilum sathanam text file thane aan.ath kanikan aan content-type header resposne il use chyunath
-->ingane chyumbol karyangal petten nadakum

==========================================================

# Cryptographic Modules
-->==assymetric il njan ithrem kalam vijarichath public key vech encrypt chyunu enit private key vech decrypt chyunu enn.ennal angane alla.rand reethiyilum namuk chyam.ie, publick key vechum encryp chyam athupole private key vechum encrypt chyam.so public key vechan encrypt chythathengil private key vech mathrame decypt chyan patu.athupole private key vechan encrypt chythathengil athinte corresponding public key vech mathrame decrypt chyan patu ok==
-->ipozhul athikam website namal edukumbol thane avar namuk avarude public key tharum.mukalil ie, https://...   ennan sthalath oru lock symbol ille avide click chyth inspect chythal namuk publi key enn kanam.athan
-->ivide ivan website in ssl certificate aakunathoke kanikunund.namal thane undakiya certificate aanengil namal aa site edukumbol notification varam untrusted aanenoke paranjit. nalla certificate kitanamengil naam online il poi namal aakiya certificate ayach kodukuka apol avar athu validate chyth tharum enit aa file ssl certificate il cherkuka.
-->namuk ariya client - proxy - application server   ingane aan main aayit ullathen.so ivide ivan paryaunath ssl ennath client - proxy(nginx)  vere mathrame chelapo undakan sadhyatha ullu. proxy - applciation server  chelapo plain text il aayirikum communicate chyuka.ini proxy - application server ilum ssl connection undakiyal ath performance ine bhadikum.so athikavum proxy - application server plain text il thane aayirikum communicate chyuka ok