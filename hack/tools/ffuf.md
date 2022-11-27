-->ffuf -w /usr/share/amass/wordlists/ -u https://www.google.com/FUZZ -mc 404,200,204,301,302,307,401,403,405,500
-->ee commandinde koode 2>/dev/null cherkam enn thonunu
--> -mc nirbhandamayi kodukanam karanam default aayi 404 illa
-->subdomains chyumbol mathi -mc ok

========================================================
## Recursion
-->recursion chyunath nokam.ie,oru path il thane veendum veendum chyunath
  ->ffuf -u https://codingo.io/FUZZ -w /usr/sh... -recursion
-->ingane chyumbol aa same endpointil thane kore pravisham test chyum ie, codingo.io/admin/FUZZ   ,  codingo.io/admin/panel/FUZZ  ... pole ok

========================================================
## Extenson
-->namuk venduna extensions check chyan aayi :
     ->ffuf -u https://condingo.io/FUZZ -w /usr/share/amass... -recursion -e .bak
-->ipol .bak extension varunathoke test chyum

========================================================
## Multiple Fuzzing
->ffuf -u https://W2.io/W1 -w /usr/share/amass/wordlist:w1 -w /usr/sh...:W2

-->ivide namal custom fuzz wors aan use chyunath.athayath FUZZ in pakaram W1, W2 enn kodukunu
-->subdomains kandethan colon ittit W2 kodukunu athupole path kandupidikan colon ittit w1 kodukunu

========================================================
## Importing Request
-->namal burp suit il poi ethengilum oru request il right click chythal copy to file enn option kanam.so ath click chyth namal aa request oru file ilek aakuka.
-->ini terminalil poi nano adich aa reqeust file open chyuka athil GET / enn kanam.so avide namal GET /FUZZ enn koduth save chyuka enit namuk ee file vech fuff chyam :
  ->ffuf -request /tmp/request -w /usr/share/amass/wordlist

-->ingane namuk directory,header,paramter oke chyan patum
f