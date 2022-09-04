1) CSP (Content Security Policy) header helps detect and mitigate attacks such as XSS and Injection
2) HSTS (HTTP Strict Transport Security) restricts web browser to access web servers over HTTP

3) Referer header -> from where the request is coming from
   ie, Referer: https://facebook.com  .  ivide namal google inte oru page ilekan pokunath.but namal pokunath facebook il ninuman athukondan Referer: facebook enn varunath ok

  vere oru situation nokam.athayath namal facebook il namude password change chyukayanen vecho apol change chyunathin thott mumb googlilek pokumbol referer header il facebook ennum koode namude username , password oke aa header il varunengil googlilek namude details pokukayan. ie, oru sensitive information is leaked to a third party

4) X-Frame-Options header prevent clickjacking
                       -> Deny enn koduthal aa page il iframing onum thane chyan patila
                       ->Sameorigin ennan kanuthengil aa origin ullath mathram iframe chyam
                       ->allow-form: Domain - like whitelist chyuna pole.some site are only allowed

5) X-Content-Type-Options -> Prevents MIME sniffing attacks
           MIME types palathum und.content-type nokiyal manasilakum eth tyep aanen.like text,json,plain,html.
chela samyangalil application mime type define chyan maranupoitundakum.ingane verumbol browser correct aayit type use aakila , transform non executable MIME types into executable