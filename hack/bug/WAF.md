# Part 1 :
-->red team aan waf bypass chyan nokuka.namal pentest chyumbol teams inod paran waf disable chyikuka
-->waf ennath epol venamengilum bypass chyapedan sadhyatha ulla sathanam aan.so waf inekalum developers internal aayi nalla oru defense undakiyitundakum.ath pwolikuka ennathan namude joli
-->chalapol WAF thane aayirikenamenila defense aayi use chyunath pakaram some kind of filetering aakam like libraries ie, CSRF token/card used to protect against CSRF attack rather than a WAF protecting them.so waf thane aano csrf allengil xss angane oro type inum waf aano atho vere enthengilum aano defend chyunath enn namal sthithikarikanam.filtering aanengil online il athinte exploit kandupidikan nokuka
-->whitelist / black listing chyth vechitundakum.so athum namal nokanam.namal kodukuna input eth reethiyil aan ath parse chyunath enn nokuka.namuk kituna response anusarich study chyuka
-->403,500 status oke response kitiyal vidaruth. 403 means forbidden athyath namale ath access chyunathil ninum entho mechanism namale thadanj nirthunund.so ath waf aakum.so ath study chyuka.500 internel server error vanalum nokanam.athil ninum enthengilum error message/info kitum

# Part 2 :
-->charecter encoding chyth test chyuka
-->ascii , utf , unicode, url, html, base63, multiple encoding oke vech bypass chyan nokuka
-->eg : `<script>alert(9)</script>`  ennath full aayi url, html, ...angane pala type aaki encode chyth test chyuka

# Part 3 (tools):
-->w3af
-->wafw00f
-->bypasswaf
-->wafninja
-->sqlmap  - eth waf aanen parayila but waf undengil waf und enn kanikum

# Part 4 :
-->oru post request eduthit intruder il iduka.enit athile ethengilum oru parameter name add kodukuka(value alla name aan liek `$submit$`)   enit namuk korach names kodukam enit attack koduthit athil kituna status code enthanen nokuka.403 oke kanikunundengil athil response il varuna ellam study chyuka angane namuk waf ethanen manasilakan sadhichekum 
-->oru post request intruder il iduka enit ellam clear chyuka enit POST ennath add chythit wordlist aayi ulla ella methods um kodukuka enit start attack chyuka.chelapo vere method il namuk request akan patiyekum.patiyilengilum kozhapam ila 403 oke varunundon nokuka.undengil waf namale anuvadikunila ennartham
-->oru post request eduth intruder il iduka.enit ellam clear chyuka.enit athile parameter name inte value add chyth ulla ella event handlers um wordlist aayi kodukuka ie `submin=$eventhandlers$` .html 5 il ulla ella event hanlers um koduth attack chyuka
-->oru post request eduth intruder il iduka enit elam clear chyuka enit content-type: add chyuka enit ulla ella type um wordlist aayi koduth attack chyuka.file upload vulnerabilites check chyuna samayath ee technique use chyam
-->oru request eduth intruder il iduka enit user-agent: add chythit ulla ella user-agent um value aayi koduth attack chyuka.chela website ukal chelapo 403 veram 

-->==oru server il aan nammal namude application upload chyunath.so namal ayakuna requests oke server aan handle chyunath.so server load balancer aayum reverse proxy aayum act chyunu. namude ela karyangalum handle chyunath server aan.namude database adakam ellam store chyunath server il aan ok==