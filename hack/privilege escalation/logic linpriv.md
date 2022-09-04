1) shell access kitiyal sudo -l adich user in enthengilum root command adikan patuon nokanam.ithine shell escape sequence enn parayum
2) ps command adich enthoke service undenum ath password ilathe open aakan patuon nokanam
3) /etc/shadow file password ilathe open aakan patumo enn nokanam.-->ls -ls /etc|grep shadow enn adich nokam apol file readabel/writable aano en oke nokan patum
4) /etc/shadow/ writable permission undeki puthiya oru hash undaki nano /etc/shadow adich root inte hash replace chyth root aayi keram
5) /etc/passwd/ file writable aanengil oru puthiya hash passwd undaki nano adich root:x: undakum athile x maati aa pasword hash itit root ayi keram
6) enthengilum files oke write chyan undenkil /tmp directory il chyam karanam athin write permission undakum generally speaking
7) sudo -l adikumbol pala binariesum kanum./usr/sbin/apache2 enn kanadal manasilakan athin gtfo bin ila so environment variable upayogikanam
8) evironment variable priv esc engane aanenal nammal nammal sudo -l il ethengilum binary run chyumbol there is a shared object (.so) that is created and run by LD_PRELOAD.
9) so ld_preload in shared object venam aa shared object nammal create chyanam enit ath nammal point chyanam binaries run chyumbol.apo root access kitum
       -->LD_PRELOAD=/tmp/preload.so apache2
	   >id         // root
10) -->cat /etc/crontab adich cronjob undon nokuka.enit ath locate chyth athile permission,owner,group oke nokanam.athinanusarich namuk exploit chyan kazhinjekam
11) chela cronjob inte variable path nokit namuk same name il vere oru file undaki first variable path il aaki exploit chyan kzhinjekam
12) SUID/SGID ulla executable files nokanam -  -->find / -type f -a \( -perm -u+s -o -perm -g+s \) -exec ls -l {} \; 2> /dev/null   .ith adich nokiyal oron kanam.ithil ulla ethengilum file vulnerable aavam apol exploit-db il ninum kandetham
13) suid/sgid il enthengilum file exucute chyumbol just binaride peru mathrma kodukunengil ath environment variable il rely chyunu enan artham so ath namuk exploit chyan kzhinjekam.eg:ethngilum oru env il avasanikuna oru file eukuka enit -->strings fulppath filename  koduthal kanan kazhinjekum athil service apache2 start enoke.ivide jusrt service,apache2 enn full path aayi koduthila so athan udheshichath
14) -->/bin/bash --version adich nokuka enit version 4.2 in thazhe aanegil ath vulnerabel aan.athupole thane namal exploit chyan use chyuna executable file il suid bit set chythitum undavanam
15) epozhum history nokanam.avide ninum priv esc chyanula passwd mato kitiyekam -->cat ~/.*history | less enn adichal kanam
16) pala type cofiguration files system thilundavum athil chelapo passwords plaintxt il undavam. -->cat myvpn.ovpn  eduthal oru /etc/openvpn/auth.txt enna oru path kanam.so avide poi ath cat chythal athil ninum credentials kitum
17) root(/) il hidden files or directories undo en chech chyuka -->ls -la /   .avide .ssh enna oru directory kanam so -->ls -l /.ssh  .ivide root_key ena oru file undakum ath user in readabel aan so ath open chyth athile key copy chyth namude machine il it ssh chyth keram -->ssh -i root_key root@ip athin mumb aa file in -x permision kodukanam.pakshe ivide mota shiva private key online il poi athinte format matitan puthiya file ile akit(root_key) ssh vech keriyath
18) 