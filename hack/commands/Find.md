-->find  enn mathram adichal aa pathil enthoke folders undo athil ulla ellam find chyth tharumen thonunu
-->find /home -name .bash_history
-->ipol /home directory il ulla ellathilum .bash_history enna sathanam find chyum ok

## find with grep
->`find /home -name .bashrc -exec grep key {} \;`
-->ipol .bashrc enna file find chyum enit -exec command vech grep (serach) chyth key enna word ithil undon search chyum ok.{ }  means all folder.athayath ella folder/files ilum nokum.angane entho aan

## which directory
-->namal find and grep vech kandupidhcaht eth directory il aan enn kanikila.ath kanikan :
->`find /home -name .bashrc -exec grep -H key {} \;`
-->ie, -H enn argument grep in shesham use chyuka ok

## Line starting from the exact word :
->`find . -name .bash_history -exec grep '^passwd; {} \;`
-->ivide '^ use chythit enth word kodukuno ath mathramayi varunath find chyum. ini namuk /etc/passwd ingane oke ullathan vendathengil '^ mati just 'word'  enn kodukuka ok ie,  ie,We can ask `grep` to only match the line **starting** with passwd by using `^`

## find setuid/setgid files/folders
->find . -perm +6000