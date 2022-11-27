-->container varunathin mumb oru app develop chyumbol aa development team il ulla ellavarum aa app undakan venda binaries(languages,database...) install chyanam.but container vannthodkoodi namuk venda binaries ee container il undakum so namal athil ninum eduthal mathi allathe ellam oronayi install chyenda avisham varunila
-->engane ellam vere aayi install chyumbol errors oke veran chance und.but container il ninum direct edukumbol valya problem varunila
-->ella container intem base layer il oru O.S (linux pole) undakum.mainly alpine aan undavuka enan parayunath.alpine simple aan polum so athinte mukalil aayi oro binaries oke undakum polum

-->medium.com site il kali il docker install chyunath und -> https://medium.com/@calypsobronte/installing-docker-in-kali-linux-2018-1-ef3a8ce3648

1) ->curl -fsSL https://download.docker.com/linux/debian/gpg | sudo apt-key add -
2) ->echo 'deb https://download.docker.com/linux/debian stretch stable' > /etc/apt/sources.list.d/docker.list
3) ->apt-get update
4) ->apt-get install docker-ce          (install ayi)
5) ->docker -v                     (docker install ayon check chyan)


-->docker image and docker container are different.docker image ennal namal evide ninano binaries oke edukunat.athayath postgrsql enna binari namuk venam apol ath namal docker image il ninan edukunath.athe samayam ee postgresql namal image il ninum eduthit namude local machin il save chyule.enitan namal aa binary run chyuka.so local machine il vech aa app run chyumbol aa run chyuna environment aa container.so container il ninan namal binaries run chyuka.so namal binary run chyumbol container environment create aakunu
-->dockerhub site il kanunathellam docker images aan containers alla.avide ninum namal image edukunu enit container il run chyikkunu
-->oru binary run chyan -> docker run postgres:10.10   enn kodukuka
-->ivide 10.10 ennath version aan.namuk venda version run chyam.locally ee version save aayitillengil ath online il ninum edukum
-->already postgresql inte ethelum version save aanengil namal vere version install chyumbol peten aakum.karanam mumb ulla version il pala layerum ipol install akuna version il und so already ullath kond illathath mathrame install chyu
-->satharan oru computer il hardware->kernal->application  ingane mainly 3 layers aan ullath. kernal aan hardware umayi communicate chyunath like cpu, ram etc... application layer il aan oro application run chyunath.oro operating systethinum athintethaya kernals und.athukondan namal linux enn parayumbol ubuntu,kali,....angane parayunath.ee ellam oru linux enna kernal il aav work chyunathengilum application layer il matam varuthum angane aan lunux il thane pala distributions um undakunath but kernal same aan.athupole windows inum athintethaya kernal und

                                                 APPLICATION
                                                          |
	                                                  KERNAL
	                                                      |
	                                                 HARDWARE
-->**docker vs virtual machine** --> docker application layer il mathraman run chyuka.so host inte thane kernal aan docker run chyumbol use chyuka.but virtual machine use chyumbol athinte thane kernalum use chyunu.ie, virtual machine run chyumbol application layerum athupole kernal um vere thane aan use chyunath.ithukond thane docker aan VM kelum fast.docker small size aan comparing VM.But VM namuk eth operating systethinte molilum chyam.But docker athintethaya OS ulla host ile run chyan patu.athayath windows kernal ann host engil namuk linux inte docker use chyan patila

=====================================================
-->njan docker il ninum ruby edukan nokit ayila ie,
->`docker run -it ruby /bin/bash`
-->so njan ->apt install docker adichit onude chythapol downloading aakunund but pinem vere entho error knaikunundayirunu