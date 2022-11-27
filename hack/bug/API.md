# 1 - Client Server Architecture
-->Namal oru site search chyumbol aadyam athinte dns look up nadakunu athinte corresponding IP kitumbol aa ip vech athinte server ilek HTTP protocol vazhi communicate chyunu.athin aadyam oru TCP connection undakunu.enit serverumayi communicate chyunu. enit server namude request backend application il ayakum.application namude request in anusarich response tharum aa response proxy server vazhi namuk kitum
-->firefox il poi google.com adikuka enit inspect til network tab il poi nokumbol namal adicha site inte details kitum athil ip adressum kanikunund
-->https://mxtoolbox.com  enna site il poi namuk venda site koduth search chythal athinte corresponding IP kitum. athuvedh https://ip koduth serach chyth nokuka

# 2 - Web authentication & Cookie
-->authentication, cookie oke namuk already ariyamalo
-->authentication il main aayi 3 ennaman ivan kanikunath ie, basic,digest,oAuth
- basic authentication ennal namal kodukuna credentials base64 ecode chyth send chyunu
- digest authentication il namude credentials encrypted aayi send chyunu
- oAuth il matoru application il ninum namude credentials edukunu
-->Json string : {"name":"john"}
here name is key , john is value
-->Json Object : {
"emmployee":{"name":"Josu","age":25,"city":"new york"}
}

here employee is an object with value of key pairs

-->Json Arrays : 
{"employee":["John","Anna","Peter"]}

-->vere example nokam :

					data: [
					{
						id:7
						name:joseph
					}
					]

ivide array und.array ude ullil objectum und.ivide oru object njan koduthitulu.but sherikum kore objects undakum

==========================================================

API VS WEBSERVICES
-->Not all apis are webservices but all webservices are api's
-->webservices il mainly XML,WSDL,SOAP oke aayirikam use chyuka.but api il eth style venamengilum use chyan patum
-->Popular webserviced protocols are :
- SOAP (Simple Object Access Protocol)
- REST (Representational State Transfer)
- WSDL (Web Services Discription Language)

Namal ivide padikan pokunath REST based webservices aan or API

==========================================================

## API
-->rand applications thamil communicate chyan use chyuna sanaman api
-->web,operatin system,databse,hardware.. angane palathum api's use chyunund
-->softwares um hardwares um thammil communicate chyan API's use chyunund
-->namal insagramil ninum oru account click chyumbol aa user inte information, images oke namuk tharunath api vazhiyan
-->REST api stateless aan.so client il ninum server ilek pokuna requests il information undayirikanam
-->rest api caheable aan.server il ninum varuna response chelapo cache chyth vekunundkam.if the data is cacheable,it might contain some sort of a version number
-->REST uses XML or JSON for sending and receivin data
-->REST calls services via URL path
-->REST api results are in plain xml or json
-->REST api transfers over HTTP only

-->https://reqres.in  enn site il poi namuk api test chyth paidkan patum ok
-->PUT, PATCH methods vech api test chyumbol already avide oru data undayirikanam athupole postman il aa correct endpoint id yum undayirikanam.PATCH use chyunathenthinenal cheriya oru portion mathram update chyan like roll number matanoke.
-->athesamayam POST vech chyumbol namal puthiya oru data undakukayan so apol aa path mathram endpoint il undayamathi

-->namuk response aayi varuna json api parse chyan upayogikuna sathanamanen thonunu "jsonpath"
-->jsonpath is a query language that helps us in parsing the json data.ith parse chyunath $,@,.. agnene oron vechan $ means root.athayath aa json data angane thane parse chyum. $.name ennanengil aa json data yile name parameter mathram parse chyum
-->jsonpath.com enna siteil poi namuk ith test chyth padikan patum


====================================================

### CDN
-->cdn ennal content delivery network.cloudflare oke CDN ann. CDN use chyunath enthinenal internet il ulla contents fast , secure, private aayi namuk deliver chyan aan.
-->Lokath eelaydathum cloudflare inte servers aaki vechitund.so namal cloudflare use chyuna oru website use chyumbol namuk aa cdn vazhi peten contents internet il ninum kitum
-->Ddos attack oke illandakan CDN sahayikum
-->website il ninum namal oru page load chyumbol undakuna loading time cdn kurakum. cdn use chyumbol images,js files oke peten namuk tharumenan parayunath