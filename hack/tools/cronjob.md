cronjob nokan:
    -->cat /etc/crontab
	
ithin kanikuna file inte location nokuka:
    -->locate file name

ini aa file inte permission,owner,group oke nokuka:
     -->ls -la /usr/../bin |grep filename

write/read oke chyan patumen kandal group nokuka.ivide namuk kitiya shell user staff group il ulathan so namuk aa file overwrite chyan patum
        -->cat /usr/../bin/filename
		-->nano /usr/../bin/filename
		ini vide reverse shell akuka .ip kodukuka.ini aa task run aakumbo namuk shell kitum

chelapol cronjob file read mathrame undaku apol ath cat chyth athile content in anusarich reverse shell kitunath chyanam.eg: chelapol athil wildcar * undakum apol ath exploit chyanam

==============================================================

#### Path Environment Variable:
-->cat /etc/crontab adikuka enit athil kanicheakm path variable start chyunath /home/usr/ il ninan 
-->so ivide rand crontab und athil overwrite.sh enn file und.so nammal same name il ulla oru file undkanam enit ee /home/user/ enna directory il kondu idanam.karanam athilan seraching first thudangunath
--> oru reverse shell script undakuka namude ip oke koduthit athan best enit save chyuka aayikolum
-->ath executable aakuka - chmod +x /home/user/overwrite.sh
-->namude kali il nc vech listen chyuka
