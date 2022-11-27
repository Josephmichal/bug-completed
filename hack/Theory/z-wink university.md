bugbounty on real website  (youtube-)
--> aadyam burpsuite il poi scope add chyuka
      host or ip range:`bugbountytraining\.com`
      host or ip range:`\.bugbountytraining\.com`
-->ini login page il poyi enthengilum adich login chyunu.so aa /post req repeater il idunu
-->apol kanam 200 ok response.chelapol credentials correct allengilum response 200 ok ennayirikum apol aa response inte bytes/or content-length: same aano enn nokuka athayath differect incorrecrt credentials kodukumbozhum content-length nokanam
-->ini ivan sql i nokunu. ie, username=a'%password=a' or a'-- , username=admin' OR 1=1--&password=a (url encode)angane nokunu apol 200 ok enn thane enan kanikunath.chelapo blind sql i undakam
-->ini namal login chyuna url il oru act=login enna parameter und athil enthengilum text koduth test chyumbol ath page il reflect aakunundon nokunu.but illa pakaram ath oru comment il aann kidakunath ie , `<!-- invalid action:adimn -->` so namal ee comment close chyth test chyanam ie,
-->admin enn koduth repeater il send adich nokanam.enit ettil xss test chyuka ok
-->nerethe thane server:nginx /1.0.2.. ubuntu ennu kandathkond thane ella parameter ilum directory traversal chyth noakam =`/etc/passwd`   =`/../../../../../etc/passwd` agane ok
-->ivan entho product order chyth so athinte order id kity ath oru GET request il order_id=NDIwg.. ingane kandu so ath decode chythapol oru number kity so aa number in pakaram vere number namal thane encode chyth aa same request il order_id= il koduth send chyunu apol IDOR nadakunu athayath vere alude order information kanikunu

namuk venduna extension install chythit namude website (burp il) right click chyth active scan chyuka apol ath full scan chytholum ok
ella parameter il ulm =&00 null byte oke itt nokanam numers letters anagen palathum iit send adich nokanam

/PATCH polula request und.password change chyanum matum ith use chyarund
/PUT enthengilum update/add chyan use chyunu
/HEAD request il /HEAD enn ittal pine namuk varuna response il response headers mathrame undaku
/OPTIONS enthanen correct mansilayita.informations oke nokan use chyan patumen thonunu ith use chyumbol

cookie header il pala cookies um athinte values um undakum.cookie names custom aayi developers koduthitilengil aa cookie name googlil poi nokiyal enth software aan use chyunath enoke kandethan patum

burp il nammal oru scopr set chythal athil namal enth chythalum aa request oke kanikum athupole firlter il :show only requested enna option select chyathe vechal namal enthegilum request chyumbol namal directly request chyatha request um kanam angane athu vazhiyum test chyan patum. athayath ivan ivide entho configuration files chyunath nokunu athile request oke nokumbol namal request chyatha request kanam athil nokumbol manasilakum /storage/config enna pathil aan namal undakuna config files save aakunath enn.so namal browser il /storage/config ennadikumbol directory indexing nadakunath kanam.athil oru .tar file kanam so ath eduth decompress chyth open chyth nokunu

use all the features click all the buttons ok.athin shesham namuk target il poi oro request um test chyam.endpoint parameters ullath aadyam test chyam like injections oke.aadyam oke ingane ulla request oke test chyam enit deep aayi keram ok.

==========================================================

### university:

#1 
-->website il pala karyangal undakum.ivide oru button und but click chyan patunila so ivan inspect element click chyth edit chyth disabled=false kodukunu apol button click chyan patunund
-->ithallathe vere reethiyilum chyam.ie inspect element click chyth athinte id=tuna ennu kanam. so console il pokuka.enit document.getElementById('tuna').disabled=false koduth chyam
-->note:document. ennal website ile pala karyangal manipulate chyan use chyunathan javascript il
-->ini athava inspect adich athil id= illengil namuk oru class="tuna" ennu puthiyath undaki console il poi chyam ->`document.getElementById('tuna')[0].style`
-->oru image right click chyth inspect element adikuka enit athile code il change varuthuka ie, `<img src= x onerror=alert(1) style='width:300px' >` 

==========================================================

#2 - firefox inspector note
-->cookie pala names undakum.so athoke note chyanam enit ?token=xxx123 adich nokuka.athayath ella webpage ilum parameter url il undakila.so namal thane url il ?cookiename=xxx123 adich ath reflect aakunundon nokanam
-->site il special aayi kanuna token names, allengil enthengilum special aayi kanunath inspect/view-source adich search chyth nokanam.aa value onnil kooduthal pravisham code il varunundon nokanam.varunundengil evide enn nokanam.ivide token value page il reflect aakunund athupole oru script tag inte ullilum varunund.apol ithupole ?token=xx123 adikumbol ath aa script ilum varunundon nokanam undengil avide xss work aakunundon nokanam eg: ?token=xxx123";alert(1)//      itt test chyuka
-->ithupole namal enthengilum search chyumbol ath evide oke varunund enn inspect chyanam

==========================================================

#3
-->username=josu%password=admin' OR 1=1--    oru space um last itto (url encode it)
-->?category=admin' OR 1=1-- (url encode chyumbol = sign encode chythum pine chyatheyum test chyth nokanam ok athayath 1=1 ile = ok)
 -->epozhum sql i test chyan sleep(10) nokam eth parameter ilum test chyam ie
                                 username:a'; SLEEP pg_sleep(10);--
                                 password:foo

==========================================================

#4 - IDOR
-->simple aayi paranjal namude ID server maryathak check chyatha avastha
-->ID ennath epozhum parameter ile oru value aayit mathram aayirikila set aaki tharunath chelapo oru path pole thane aayirikum ie, GET API/v1/user/12345   ithil 12345 aan ID so ee id change chyth nokanam IDOR undon ariyan
-->IDOR cookie ile oru value aayitum veram like cookie: session=....; user=z-wink;
-->chelapo x-user:z-wink enna oru http header il aayirikam ID ullath
-->oru situation nokam->namal login chythu so namuk apol oru session cookie kititundavum.ini namuk password matanam.so angane chyumbol /POST req aan enn namuk ariyamallo.ettavum thazhe nokiyal kanam password=,newpassword= parameter but athinte koode email= parameterum kanam.request il nokiyal namude session id cookie athil ullathayi kanam.so password matumbol session cookie request il undengil pinne enthinan namude email chodikunath?athinte aavisham ila karnam session id il namude details und.so aa email parameter il vere aarudengilum email koduth oru password set chyth account takeover chyan patumon nokanam.ok
-->so REMEMBER epozhum
-->so burp il namal test chyumbol parmeter pole evidengilum identifiers undon check chyanam. ie,id=1234. karnam namude session id il namude id,email..oke undakum so veendum oru parameter vech namude id check chyenda karyam ila so angane verumbol avide IDOR undon check chyanam ok
-->ingane undakumbol aadyam aa id= empty aaki send chyanam.apol error vannal athinartham server ee parameter enthayalum check chyunund ennan apol ee id il vere value itt nokanam ok
-->rand account namal undaki athil check chytha mathi
-->/POST request il oke eethavum thazhe aayi { }  itt palathum test chyam like json pole ie,
                        {
                           "data":{
                                  "userID":1234,
                                  "newemail":"z-wink@gamil.com"
                                  }
                        }
                    ithupole enthengilum itt nokuka.prathyekich email,passwd change chyuna url il okke

==========================================================

#5 - complex IDOR with intruder clusterbomb
-->/POST,/PUT polulla request il IDOR bruteforce chyth nokumbol sredhikanam.veruthe data save chyth ddos aakandirikan ok
-->ipozhulla website il oke ID=12345 ennayirikila complex aaya strings aayirkum like - 2BTXYi1 apol engane IDOR check chyam enn nokam
-->so ee id sredhiku 2BTXYi1 ivide numbers,letters (capital and small) use chyunund.lastethe randennam nok.etavum last number ,athinte backil small alphabet so ee request intruder il iduka
-->enit 2BTXY$i$$1$ enn randinum add kodukuka enit type cluster bomb kodukanam
-->ini payload type bruteforcer kodukuka.enit aadyathethil a-z (small.karanam aa letteril small letter mathram aayirikam randomly set aakuka)vere kodkukuka randamathe payload 0-9 kodukuka(athil numbers mathram aayirkam varuka)
-->randilum length 4 ullath mati 1 kodukuka eni resourse pool il poi cuncurrent 1 kodukuka veruthe ddos aakandirikan ini start attack kodukuka
-->result il 302 verunundengil ath working aayi ennayirikum so sredhikuka.

==========================================================

#6 - CSRF and cookie based authentication
-->nammude cookie extension open chythal athil thazhe aayi httponly , session,secure,host enn kanam athin ellam ticked aano enn nokanam.athava ticked allengil ath oru vulnerability aan.if secure ticked allengil ath TLS illa ennan artham means data plain text il transfer aakum so MITM attack chyan sadhyadha und
-->oru website il cookie alert il kanikumo enn nokan inspect->console->alert(document.cookie) ctrl+enter click chyuka ok
-->burp il email change chyuna request il right click chyth generate csrf poc ennath click chyth email vere itt athinte response url eduth browser il test chyth nokuka.apol email marunundon nokanam
-->email ,password oke change chyumbol csrf=-sdkfbkdfnksdfn  undayekam but ath correct aayi implement chythitundavenamenila so ath nokanam
-->csrf=sdfdslj ath angane thane remove chyth send chyth nokuka
-->nalla csrf aanengil namal email change chyuna request send chythal kitiya response il puthiya csrf aayirikum undavuk.athupole nalla csrf aanengil ath session cookie yumayi mingle chythitundavum ennan parayunath
-->emailchange=sfsdfsa & csrf=sdfjsldf   ennath /post maati /GET aaki athile pathil aakanam ie,
      GET my-account/change-email?emaichange=sdfsd & csrf=sdfdjf  send adikuka enit enit ee csrf=dsfdsf angane thane remove chyth verum emailchang=sdfj mathram itt noki send adikuka.apol email change chyunundon nokanam. /POST my-account/change-email ennan undayirunath marakanda

==========================================================

#7 - tresure hunt
-->css request um namuk nokam athilum chelapo valla comments developers chyth vechekam
-->burp collaborator edukuna avide burp search enna option undakum athil namuk palathum serach chyam like password ennadichal aa word evide oke undo athoke kanam athil enthengilum info undengilo.credentials oke nokan ee search feature use chyam

==========================================================

#8 - Target Reconnaissance & Approach
-->js link finder,param miner enna extension install chyth vekuka
-->site:usa.com -www.usa.com          (subdomain kandupidikan by dorking)
-->site:usa.com -www.usa.com -mall.usa.com -hello.usa.com (apol ee mall. , hello. varunathoke result il kanikila)
-->site:usa.com "admin"       (specific string vech nokunath)
-->subdomain finder enn googlil search chythum subdomain kandupidikam subdomainfinder.c99.nl enn googlil search chyy
-->terminalil poi ->ping twitter.com adikuka enit athil kanikuna ip address eduth https://[ip]  koduth search chyuka apol oru notification pole kanikum engane oke mathram namuk ee siteil il keramenn like twitter.com or www.twitter.com enn ok
-->ingane check cheyumbol certificate il nokiyal namuk additional subdomains chelapo kanam. apol athum namude target list il itt test chyam
-->ipinfo.io enna site il poi ee ping chyth kitiya twitter ip address koduth search chythal namuk kooduthal informations kitum  like  route:"104.244.42.0/24"  so ee ip range eduth bruteforce oke chyth enthengilum oke kandu pidikan patumon nokuka
-->googlil waybackmachine enn search chyth namude targer url koduthal aa site epozhoke archive chythu ennath kanam.ivide ivan 2006 il twitter engane und enn kanich tharunu.aa calenderil kanuna blue colour ile click chythal kanam
-->waybackmachine use chyumbol pand aa site engane und enn ariyan patum athupole ipol ulla aa site il pandathe pala karyangalum ipozhum undayekam.ivide ivan oru site ithupole waybackmachine use chyunu enthinanenal aa site ile oru page il oru url vechitula expoloit aan.so  endpoint kandethi but paremeter areela FUZZ chyth kandethan pateela so waybackmachine vazhi parameter name kandethi.engane kandethi ennal aa same page aa archive version ilum use chyapettirunu.so kandethan patti

==========================================================

#9 - Hunting Authentication Bypass in Bug Bounty
-->namal oru site il namude bio add chyunu enn vecho angane add chyumbol namude identity nokitan ella site um chyanath ithan authentication.athayath ee request ayakunath namal thane aano enn ariyan
-->ivide ivan oru bio add chyunu enit athile request repeater il idunu.enit athil kore cookies kanan patum.ivan oro cookie um remove chyunu enit send adikumbol bio add akunund.namuk vendathum ath thane aan.so angane avasanam oru cookie mathram aayi.so athin artham aa cookie aan authentication process chyunath.aa session cookie aan server inod paryunath that we are allowed to do that
-->ini autorize enna extension install chyth vekuka
-->enit athil ee cookie angane thane copy paste chyuka.ini namal browser il poi enth request chythalum ee autorize screenil aa request ile cookie kk pakaram ith replace aakum.ingane namuk IDOR oke nokam ennan ivan paryunath.
-->original request inteum modified requets inteum length same aanengil ath bypass chythu ennan artham ennan ivan parayunath
-->x-admin:true enn koduth bypass chyan patunundon nokanam.athinte koode x-ip:127.0.0.1 koduth nok

==========================================================

#10 - intro to  Cross-site-scripting
-->namuk site il inspect element adich ethengilum `<div>` right click chyth edith chyth ath angane thane remove chyth `<a href="https://google.com">visit google</a>` enn aakan patiyal ath html injection aanenan ivan parayunath.ithil thane xss um try chyanam like 
`<a href="#" onclick="alert(1)">visit google</a>`  .ee event aakunilengil vere event nokanam
 `<a href="javascript:alert(1)">visit google</a>` .inganem test chyth nokam
 -->chelapo image mathrame inject chyan patu apol->`<img src="x" />`  itt test chyth nokuka apol screenil kanan patum injection aakunundengil
 -->so `<img src="x" onerror="alert(1)" >` itt xss test chyuka
 -->xss chyumbol baaki ullath rand reethiyil chyam onn // itt comment chyam illengil baaki ullath oru variabile il aakum lik x="  enn ittal baki ullath x inte value aayi marikolum.onnil kooduthla paranthesis itt nokuka  like alert(1)));  angane enthengilum oke try chyanam

==========================================================

#11 - Using Burp Intruder for Rapid Target Recon
-->googlil poi subdomain finder il ninum namude target inte subdomains kandethuka enit ath notepad++ il paste chyuka.uneneccesary sathanangal remove chythit openoffice calc enna software use chyth ath paste chyuka
-->enit target site il ninum enthengilum /GET requets eduth intruderil viduka
-->enit mukalillula target: enna sthalath thane add kodukuka ie,`https://§mydukaan.io§` enit payload il nerthethe subdomains kodukuka enit resourse pool il poi maximum concurrent : 500 kodukuka(karanam 500 subomains aan ullath athukond.500 req ottadik poyal ellam block chyan onum patila athukond)
-->ingane chyumbol enthan nadakunath enna ee websites ellam port 443(defualt https inteth) request chyum
-->start attack chyunathin mumb update host header to match target ennath tick itt vekuka apol namal add chytha sthalath oro subdomains um varumbol host header ile valueum ath thane aayi marum
-->==update host header to match target ennal target um host um same valuee aan ok==
-->ini namud position il poi `target : https://$twitter.com$:8443` (chela samayangalil web port aayi ithum use chyarund)enn koduth start attack chyam.ingane pala port um koduth attack chyan like 8080 (aakumbol` http://$subdomain$:8080` enn kodukam) , 80 ...,https ullath http mathram aaki nokam.angane oro port il enthengilum run chyunundon nokam.enit result il status(200,301,500...) enna oru bar undakum athil onum kanikunilengil onum illan artham.athayath ethengilum port open aayi kidakunundonanen thonunu check chyunath areela.enthayalum nokiko. athupole ini body il vannal 
-->`target:https://$domain$` koduthal enthan sambavikuka ennal host: headeril ee subdomains oke thanale vanolum but update host header to match target enna option tick itt vekanam.ingane ee /GET request il oro subdomains um check chyam
-->ith koodathe host: header injection um chyam like body il host:twitter.com ennath mati twitter.org aaki attack chyam.(`target : https://$subdoman$` enn koduthit.NOTE: update host header to match target uncheck chyanam.apol oro sunbdomain um request chyumbol ee twitter.org enna sthalath ninan varunath enn thonikan aatum aan)
-->ipol namal subdomains intruder il payload aayi itt chythu ithupole oro subdomains inum ip address undakum so oru ip eduth ipinfo.io il poi iprange nokuka so ini nerthepole `target:https://69.145.183.$2$` cluster bomb select chyuka enit payload type numbers kodukuka enit 1:255:1 enna format kodukuka enit start attack adich nokam.angane oro ip ilum entha nadakunath enn nokam
-->NOTE: ip vech bruteforce chyumbol side ile update host header to match target tick italum illengilum ore result thaneyan tharuka ok.
-->ee kitiya subdomains orornum check chyumbol google/duckduckgo il poi ==site:subdomain "token" or "/token"== angane adich nok.       angane oro keywords use chyth search chyuka.
-->ivan ingane oru subdomain search chythapol` www.subomain.com....?token=sdfkhsdkfhsd..` kandu so ath click chythapol user inte billing details matum oke kananum ath manipulate chyanum oke patumayirunu

==========================================================

#12 - Picking a Bug Bounty Program
-->kore scope ullath 
-->old aayitula targets so pandathe archives il ninuum(waybackmachine) details eduth paniyunath
-->xss,idor oke test chyumbol thane namale logout,block oke chyunengil ath il kooduthal neram nikendena ivan parayunath
-->IDOR test chyumbol cheriya id aanengil nokam pakaram sdfoihg-sdfhkhdsfhds-sdfhsjh  ingane oke ula valiya string aanengil noki samayam kalayanda

==========================================================

#13 - Intro to GraphQL Penetration Testing
-->bypass waf ,403 bypass extensions ivantel kandu so ath install chyth vechek epengilum use aakum
-->ivide /grpahql il namuk IDOR , injection(sql),authentication type vulnerabilities oke chyan sadhyadha und
-->json form il aan data undakuka.so athil "id":1  enn kandan ath mati 2,3 oke aaki IDOR check chyam angane enthokeyo chyan
-->==NOTE:graphql case sensitive aan.so String ennoke idumbo s capital akanam ok==
-->query is like a /GET request.it pulls data most of the time.it retrieves data like in /GET request
-->mutation is used to change something like /POST,/PUT,/PATCH,/DELETE requests
-->introspection query public aakunath nallathala.karanam athil ninum namuk manasilakan patum appliation enthoke requets oke aan nadathunathen
-->satharana namal graphql il variables: , query: ennath kanan patum.ithil variables epozhum undakanamenila.query variable support chyunundenil mathrame variable idenda aavisham ullu ok ie,
````
{
"variables":{
	"accountid" : "12345"
	},
	"query" : "query zwink($accountid:string!) { getuser(accountid:$accontid ) 
               {email}  }"
}
````

-->ivide kore karyangal sredhikanam ie,query kk sheshamvarunath namal change chythalum prathyekich error onum varila ie,ivide zwink ennaht josu aakiyalum onum sambavikila.ath query name aan.namuk enth perilum vilikam application error varila ok.
-->variables namuk enthum kodukam.datatype mathram sredhichal mathi. "a":"1234".string aanengil urapayum numbers aayit indavula athinte koode " undakum.so angane namuk ishtapetta varibale in datatype anusarich value kodukua ok
-->ini query zwink in shesham bracketil ulla dollar sigh ennath aa variable.ath namaledukunu athin shesham ulla colon itt koduthath data type aan.ivide string enn kodukunu karnam accountid varible inte value "12345" ennath string aan.athinu sesham ! sign idunu.REMEMBER ivide value string aanen vech string! enn thane aayirikanamenila datatype.developers chelapo athine value vere enthengilum akiyitundakum like :accountid! enn thane aayrikum datatype undavuka.so namal ithoke test chyumbol enthengilujm oru cheriya error vanal ellam pokum
-->ini {getuser..} nok. ithan sherikum query.athayath namuk user information aan vendath.so getuser kodukunu.athil bracketil accountid enoke kanam athayath namude user id aan avide point chyunath ie,12345.so 12345 enn user id ulla user inte email aan namuk vendath.athan last email enn vere bracket il kanunath.ini phonenumber aanengil (email phonenumber) enn undakum ok
-->ethengilum graphql playground eduth namude kayil already ulla introspection query response copy chyth burp intercept chyth graphql playground inte reponse il copy chyth nokiyal namuk graphql quries nalla reethiyil site il kanan patum ok
-->avide vech shema edukuka enit ethengilum query select chyuka.athil etavum mukalil kanam 
domain(
name: string!
): domain

so ivide Domaind ennathan namude mukalile example ile getuser.name ennath getuser in shesham ulla bracketile adyathe accountid.ini namude graphql playground il nokiyal kore fileds undakum athan namal etavum last ulla bracket il kodukendath ie,namuk venda sathanam kodukuna bracket so query ingane undakum :-
```
{
"variables":{
	"accountid" : "https://google.com"
	},
	"query" : "query zwink($accountid:string!) { domain(name:$accontid ) 
               {id name}  }"
}
```
-->ivide id, name (last ulla bracket) aan field il ninum namal eduthath ok
-->ingane namuk idor,injection oke nokam
-->ivde variables il "accoutid" : "https..ogool.com ; SELECT sleep(5) "  angane oke test chyam ok
-->athikavum graphql post request il aan nadakuka.ennal GET request ilum graphql nadanekam.apol namuk athil csrf ok try chyam.athayath GET /graphql?query=lfjjl ...
-->note:autorisatoin : bearer header aan application use chyunathengil nadakila pakaram cookie based authentication aanengile GET vech csrf oke nadaku
```
function JSON_to_URLEncoded(element,key,list){
  var list = list || [];
  if(typeof(element)=='object'){
    for (var idx in element)
      JSON_to_URLEncoded(element[idx],key?key+'['+idx+']':idx,list);
  } else {
    list.push(key+'='+encodeURIComponent(element));
  }
  return list.join('&');
}
```
-->ee code eduth browser->inspect->console il poi paste chyuka enit console il json_to_urlencoded ennadikuka apo automatic aayi verum enit () bracket ittit introspcetion query angane thane paste chyuka apol namuk ath url encoded form il kitum.so ath eduth GET /graphql?query=paste here chyuka.enit send adich nokuka apol namuk kanam GET support chyunundon.athava response ok kitiyal csrf oke try chyth nokanam.karanam athikanam graphql request il csrf token onum undakila ok.
-->ingane aakunilengil decoder il paste chyth url encode chyth nok 
-->burpsuite il graphql test chyumbol "variables":{..}  enna sathanam remove chyth direct aayi namuk query chyam ie,
```
{
	"query" : "{celoElectedValidators(blockNumber:12345){smartContract{name abi addressHash}}}"
}
```
ivide namal varibales implicitly kanikathathkond direct aayi 12345 value koduthu.note: 12345 in mumbilula blockNumber ennath shema yil ulla real argument aan.so argument name namuk ariyilengil nadakila ok
-->

==========================================================

#14 - DOM XSS - location.search to IMG tag
-->document object model. xml,html documents in venditulla oru api aan

==========================================================

#15 - Recon Sub-domains with Intruder for Auth Bypass
-->subdomains enumerate chythit ella subdomain um copy chyth intruderil idanam.aadyam t`arget: $https://twitte.com$` idanam enit `GET /$important-files$ `idanam.
-->cluster bomb select chyanam.enit aadyahtha payload aayi ee subdomains kodukanam
-->randamathe wordlist aayi github il ninum importantfiles.txt idanam enit resource poolil poi
100 koduth url encode untick chyth attack chyam
-->ingane files/endpoints oke fuzz chyam
-->ithupole namuk kitiya cookie: , authorization: place chyth aa same cookie matu subdomains il attack chyumbol work aakunundon nokuka
-->chela samayangalil server cookie undone noku ath correct aano enn check chyenamenilla
-->`target : https://$sunbdomains$`  itt attack chyumbol chelath 403 polulath kanikum apol angane ulla request il oke namuk kitiya auth cookie,token oke koduth bypass chyan patumon nokuka

==========================================================

#16 - Approaching a Public Target (Pinterest)
-->subdomains eduth intruderil itt oru GET / HTTP/1.1 req eduth `target:$https$://$pintrest.com$`
koduth clusterbomb select chyuka.
-->first payload http,https kodukuka
-->second il ee enumerate chyth kitiya subdomains iduka ennit resource pool il poi max concurrent req:500(subdomains inte athe length kodukuka)
-->http:// inte result il namuk vendath redirect illathathan (200 angane ullathoke check chyanam).karanam athil ninum sensitive informations kitam karanam http il encryption illa.so check chymbol aa request il ulla http headers note chyanam
-->ini https:// il nokiyal ellathilum status kanikila.so status ath ethhanengilum(200.,300.400.500) ath kanikunundengil athil ninum response kitunu ennan artham.means it is responsive so aa responsive aaya subdomain ellam copy chyth edukuka karanam athil aan namal hacking chyan pokunath ok
-->copy chythath namude spreadsheet il iduka enit hack chyam
-->so ithil eeth subdomainil ninum namuk bug kandupidikam
-->way back machine il poi namuk venda subdomain koduth check chyam
-->kitiya subdomain il 403 varunath broken auth indon check chyam. 403 bypasser enna oru extension und athil poi ee 403 ulla subdomains check chyam
-->200 status code kanikunath satharan use chyuna sites aan athil ella vulnerabilites um check chyam
-->nerit twitter.com il poi account undaki hack chyunathilum nallath ingane chyunathan.karanam mattu hackers ee reethiyil aan chyunath.namal epzhum different aayi chyanam
-->ini ivan secret files aan check chyunath/directory listing.athayath oro subdomain ilum `/GET /$directory$ HTTP1.1` request eduth importantfiles.txt itt files/endpoints check chyuka.chyumbol resource pool il poi max :100 akiko(enit ith 100 aakathe normal aayiyum chytho). namuk vendath 200 status code aan
-->ipol nadakunath phase2 enn parayam.ivide namal individual aayi oru subdomain um test chyunu
-->duckduckgo il poi site:brand.pintrest.com adich search chyuka athil vere endpoint ulla urls kanikum enit athil test chytho
-->xss allengil enth check chyumbozhum isnpect element eduth network open chyth chyumbol (athayath namuk oru image upload chyanam) request nadakunundo enn ariyanam athava oru request um nadakunathayi network il kanikunilengil ath client side il aan karyangal nadakunath enn manasilakam
-->epozhum burp ile target bar nokanam.karanam athil namal reqeust chyatha urls um kanikum apol namuk peten aa pathilek pokam
-->ivan ivide ingane nokumbol /node enna oru endpoint kandu so athilek poi `(brand.pintrest.com/node)` poi athil enth click chyumbozhum email , passwd chodikunu.so authentication bypass technique chyan nokuka 
-->so oro subdomains inum pala files/directories undakum so ath kandupidikuka.athupole kore api request undakum ath nokuka athil orornilum check chyuka ok

==========================================================

#17 - Testing File Upload Dialogues
-->oru action chyumbol ie, /POST (uploading image polethe) request il poi oro karyangal remove chyth eeth karyam aan server check chyunath enn nokanam
-->ie, extension(.jpg) remove chyth nokuka enit image upload aakunundon nokuka
-->content-type: remoe chyth nokuka
--> image format il first line ennath header aan so aa first line angane thane remove chyth image upload chyan patunundon nokanam
-->extensin gif,png,tiff,svg anagne pala extensions itt file upload chyan patunundon nokanam
-->ivide content-disposition: filename=fulllogo.svg adich nokuka
--> response ok aanengil ee content-disponsition:filename=fulllogo.svf kk thazhe athinte content kodukua sthalath oru svg malicious code kodukuka
-->svg tag inte ullil`<script>alert(2)</script>` xss okke test chyam
-->upload scanner enna oru extension und athil ee reaquest itt test chyam

==========================================================

video - Find XXE with Burp Suite Intruder
-->namuk content-type: header intruder vazhi bruteforce chyth check chyam
-->oru request kitiyal athile content-type mati nokikua enit athupole athile contents il xss polula karyangalum chyth nokuka.(athayath /post request il  etavum thazhe alle credentials undakum avide oke xss oke test chyuka)
-->eth /POST request venelum edukam enit athile content-type:$add$ kodukuka enit github ilnino mato content-type worlists edukuka enit url encode uncheck chyth resource poolil poi max:100 koduth attack chyuka apol namuk kanam patum ethoke content-type aan support chyunathen
-->ivide application/xml support chyunund so namuk xxe test chyam
-->ivide reqest body il already oru json code und.namal nerethe test chythapol kandu food enna oru parameter/tag und athile info reflect chyunund
-->so content-type:application/xml koduthit last ulla json remove chyth `<food>test</food>` koduth send chyunu
-->apol cheriya error varunu karanam xml okr oru parent element undakum so `<something><food>test</food></something>` koduth test chyumbol akunund
-->so ini portswigger il poi oru xxe payload edukuka like etc/passwd kanikunath
-->enit ee code inte mukalil aayi koduthit test in pakaram &xxe; enn koduth nokuka'
-->apol password kanikunund
-->so json format varuna request il oke ee techinique test chyuka
-->chela samayam ingane chythal nadakila apol ee /etc/passwd enn kodukunathin pakaram `http://localhost,127.0.0.1`, or ip range kandupidikuika like 192.168.0.1 polethe .
-->allengil burp collaborator use chythum nokams

==========================================================

video - # Let's Hack GraphQL
--> queries use chyunath data fetch chyan aan.database il ninum namuk venda datas edukan
-->mutation ennath data edit chyanum puthiyath save chyanumoke aan
-->Fragments allow you to decide list of fields and request multiple queries use the same list. It is usef for comparison
-->https://graphql-demo.mead.io  enna site il poi namuk kitiya graphql inte introspection athil aaki test chyan patum
-->satharana introspection query namuk kitila.athupole ella website inum athintethaya graphql playground indakum athum namuk available aakila.ithoke public aayi available aakunath nallathalla
-->epozhoke namal allCards(...): cardConnection!    ithupolula queries kanunuvo apol thane manasilakanam ith variables edukumen.karanam bracket il moon dots vech namal manasilkanama ok.oru function variables edukunathpole ith edukum
-->graphql test chyan namuk vendath :
```
{
"variables":{
	"" : ""
	},
	"query" : ""
}
```
ihan namuk vendath.ivide namal manually oron test chyum(kitiya introspection vechit ok)
-->queries test chyuna samayath post mati GET aaki test chyuka like GET /graphql?query=&variables=  angane ok.
```
{
"variables":{
	"id" :"1"
	},
	"query" : "query celo($id:ID!) { Node(id:$id) {id following{node{id}}} }"
}
```
onnil kooduthal field il deep aayi pokumbol mukalil kanunathpole chythal mathi ie,...id:$id) {id following{node{id}}} }" ok
-->ella query kkum variables venamenila.so varibles ilathathanengil :
```
{
"variables":{
	},
	"query" : "query josu{config{sorarekey}}"
}
```
ingane mathram ittal mathi.varibales ilathathkond vere onum venda ok
-->ella graphql querie names um javascript umayi connection undakum.so ethengilum oru query name eduth burp il search chyuka enit ath ethengilum js file il undon oke nokanam ok
-->