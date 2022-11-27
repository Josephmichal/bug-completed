->`curl url`
-->curl vech chyumbol url single qoute il idunath nallathayirikum
->`curl ptl-979a4382-56d06c74.libcurl.so/users/1 -H 'Accept: application/json'`

## cookie add chyan
->`curl http://ptl-49567cdb-44a8315b.libcurl.so/pentesterlab -H 'cookie: key=please'`
-->eth header add chyanum -H  use chyanam.ivide cookie header il aan namal key enna cookie add chyunath

## post reqeust 
-->curl https://google.com -X POST --data 'key=please'      or
-->curl https://google.com --data 'key=please'


## headers
-->`curl http://url -H 'accept-language: key-please'`
->``curl http://ptl-49567cdb-44a8315b.libcurl.so/pentesterlab -H 'cookie: key=please`

## canonicalise
-->namal kodukuna request curl chelapo filter chyum.so namude request angane thane curl ine kond read chyikan `--path-as-is`  enna argument use chyanam 
->`curl http://ptl-e3167fb2-612dafbc.libcurl.so/pentesterlab/../pentesterlab --path-as-is`
--illengil vere argument und `--request-target`. but ith kodukumbol path kodukunathin mumbayit chyanam ie,
->`curl 'http://ptl-e3167fb2-612dafbc.libcurl.so' --request-target '/pentesterlab/../pentesterlab' --path-as-is`

## File upload
-->file upload chyna `-F`  enna argument use chyanam. athin shsham "paramter=@filename"
-->filename local system thil ninum kodukunaht kond filname inte mumbil aayi @ idanam ok. eg : 
->`curl http://ptl-d0e30f9d-de0ef8ec.libcurl.so/pentesterlab -F 'file=/Documents/pentesterla/HTTP/@file.txt'`


## trace
--> curl il `--trace-ascii - `  enn koduthal kooduthal info kitumen thonunu.ivide file upload chyuna command il ingane chyunun
-->-F vech namal file upload chyunu. ennal post request oke chyumbol --data aan use chyunath apol athinte koodeyum namuk file add chyam like `--data @josu.txt`  ok
