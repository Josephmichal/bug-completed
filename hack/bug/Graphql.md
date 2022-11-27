-->Graphql is an alternative API for the standard REST/SOAP
-->it is a query language for apis, used to interact with the api and fetch datas from the backend through apis
-->it is much more efficient than the REST api

### REST vs GraphQl
-->rest api endpoint :
      ->/users/id
      ->/users/name
      ->/users/address

-->GRAPhql endpoint :
      -> Query {
             users
	             {
		             id
		             name
		             address
		             }
		}

-->ivide rest api il namuk moon endpoint use chyendivarune details edukan.but ivide graphql il oru endpoint vech ella details um edukunu
-->REFERENCE -> [https://apis.guru/graphql-voyager/](https://www.youtube.com/redirect?event=video_description&redir_token=QUFFLUhqbEktWWdBWVdsbUJhdG1IcXQzOWNNdV9obWxiUXxBQ3Jtc0ttZVFaQ2s1OGdzRmhUU1plb2lPakltZERNcWo3aENKNXBCQXFrUEZvUlMyMmFjWFRZWi1HelJIUUNSdjc3Z0s2dXNCbjdoWjdjQzFsNzR3Q19CR2t0QXVMaldJdXR4M0VZdHpETE5GVzdFdy1oY21Mdw&q=https%3A%2F%2Fapis.guru%2Fgraphql-voyager%2F&v=iSZ0RrCrpf4)
-->ee link il poi nokiyamathi
--> TEST # 1 -> introspection query (molile link il poyamathi vaicho)
--> TEST # 2 -> Broken Acess Control / IDOR 
--> TEST # 3 -> Dos via malicious queries - athyath same query thane oru 10000 pravisha copy 
       paste chyth send chyuna paripadi
--> TEST # 4 -> Sql/noSql injection

=================================

-->https://graphql-demo.mead.io  enna site il poi namuk kitiya graphql inte introspection athil aaki test chyan patum

-->==graphwoof enna tool github il und athvech namuk graphql enumerate chyam.angane eth library aan graphql use chyunath angane oke ulla karyangal manasilakam ok==
-->graphql endpoint kandethan:
  -> python3 main.py -d -t http://explore.celo.org/
-->endopoint kandethiyal namuk kooduthal enumeration chyam like fingerprinting
  ->python3 main.py -f -t https://explore.celo.org/graphql
-->ethoke sites aan graphql use chyunathen ariyan ->https://stackshare.io/graphql