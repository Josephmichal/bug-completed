-->grep vech namuk pala karyangalum search chyan patum.eg:
->`find . -name .bashrc -exec grep export {} \;`


## remove some lines
--> -v enna argument use chyth remove chyan patum
->`find . -name .bashrc -exec grep export {} \; | grep -v GCC_COLORS`

## Line starting from the exact word :
->`find . -name .bash_history -exec grep '^passwd; {} \;`
-->ivide '^ use chythit enth word kodukuno ath mathramayi varunath find chyum. ini namuk /etc/passwd ingane oke ullathan vendathengil '^ mati just 'word'  enn kodukuka ok. ie,  ie,We can ask `grep` to only match the line **starting** with passwd by using `^`