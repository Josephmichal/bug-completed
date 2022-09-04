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