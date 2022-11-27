What is inetpub?
What is Inetpub? Inetpub is a folder on the C drive of your Windows that contains web contents and web apps along with working as a default folder Microsoft IIS. Do you know what IIS is? Its full meaning is Internet Information Services.linux il /var/www pole

---------------------------------------------------------------------
oru mobile inte ip,mac kitiyenn karuth athine hack chyan patila.same networkil aanengil mathrame patoo.phones ip addresses change everytime they switch networks.

---------------------------------------------------------------------
username,password kiti enn karuthi ssh chyanda karyamonum ila.already reverse shell undeki -->`sudo su ,-->su [username]`  koduth keriya mathi ok.

--------------------------------------------------------------------

### canonical link tag:
-->ella website ile chela page ukalik ie,home page edukam.oru link mathramayirikilla
-->eg:         https://joseph.com
                   https://joseph.com/index.php
				   https://www.joseph.com
				   http://joseph.com
				   http://www.joseph.com
-->ingane oru page in thanne pala urls undakum apol google crawl chyumbol ithellam edukum.enit ithile ellam duplicate aakum.karanam google in areela ethan original url enn.
-->so namal ethan original enn aakan ee ooro link ilum back end il poi code chyanam ie,         `<link rel="canonical" href="https://joseph.com" /> `
-->ingane baki ulla ella url ilum ittal google in manasilakum ithan yathartha link enum baki ellam duplicate aakanam ennum
-->so nammal xss il okke " qoute okke itt code beak chyuna pole break chyth namudethaya code oke itt xss trigger chyan patumon oke nokam
-->ie , https://joseph.com/forums//index.php?u=/user/profile/1"%20onerror="alert(1);                enoke itt try chyam
--> apol ith html il -> https://joseph.com/forums//index.php?u=/user/profile/1"%20onerror="alert(1);" />   ingane varum
-->ivide xss lab il (lab-12)  nammal->host?%27accesskey=%27x%27onclick=%27alert(1)
-->The accesskey attribute in HTML is **used to set a shortcut key to activate or focus on an element**
-->so access key x koduthit alert(1) enn kodukumbol nammal site il :
                         
    On Windows: ALT+SHIFT+X
    On MacOS: CTRL+ALT+X
    On Linux: Alt+X

-->ithile pole adichal alert pop up aakum


=======================================================
### binary evide vechum execute chyan:
-->download chyth vecha app --> ./sublist3r ennath --> sublist3r ennakan:
-->ln -sf /opt/sublist3r/sublist3r.py /usr/bin/sublist3r
-->ipol aa binary ee /usr/bin il aakum ini evide vech ith ie -->sublist3r ennadichalum work aayikolum

========================================================

 burp pro windows --> https://github.com/CyberCommunity03/Burp-Suite-Installation
    OR  googlil github.com CyberCommunity03 enn search chyu

==========================================================

-->whitelist->oru list undakum ee list il ulla karyangal mathram accept chyuna reethi.ee list il illatha karyangal request il vannal block chyum
-->blacklist -> ee listil ulla karyangal vannal accept chyila block chyum

==============================================================

AWS -> 
-->S3 -> amazon s3 is a an object storage service that stores data as object within bucket. objecdt means a `file`.
-->bucket -> a bucket is a container (folder) for objects (files) stored in amazon s3
-->ee s3 vechan pala valya applications um run chyunath 

========================================================

nammude vitil oke ulla routers modems in oke main aayi TCP/UDP protocols okee ariyu so puthiya oru protocol oke undakiyal ath ith vech work aakanamenila.so namal HTTP ide improve chyuvanengil thane ee TCP/UDP ove vech thane updation ndathendi varum namuk vere vazhi illa.karanam ee internet um user thamil ulla communication inte idayil ithupole kore boxes work aakunund ie,routers,modems,firewall etc.. so ee sathanangal oke namal software update chyunapole epozhum update chyan patila.ee sathanagal illathe namuk communicate chyanum patila.so namal HTTP oke update chyumbol ith consider chythit venam update chyan.so we are stuck with TCP/UDP.

Alt-Svc: response header -> athayath namuk ariyam https ennath TCP il run chyuna port aan.but HTTP/3 ennath namuk ariyam UDP il aan run chyunath.so apol https il engane HTTP/3 protocol run chyum enna chodyam veram.apol namuk response header il ee alt-svc: response header koduth namuk matoru port allengil origin value aayikodukam apol aa site engot pokumayirikum.so agnane client aa response cache chyth vekum so ini namal aa site ilek pokumbol HTTP/3 varuna aa response namuk kitum

==========================================================

WORDLISTS -> https://github.com/kkrypt0nn/Wordlists

==========================================================
