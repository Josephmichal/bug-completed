> subfinder -d domain.tld -all -o .temp/subfinder.txt
> 
> sublist3r -d domain.tld -e baidu,yahoo,google,bing,ask,netcraft,threatcrowd,ssl,passivedns -o .temp/sublist3r.txt
> 
> findomain -t domain.tld| sort -u | tee -a .temp/findomain.txt
> 
> assetfinder –subs-only domain.tld | tee -a .temp/assetfinder.txt
> 
> amass enum — passive -d domain.tld -o .temp/amass.txt

======================================================

> cat .temp/*.txt | sort -u | grep -i domain.tld | tee -a all.txt
> 
> cat all.txt| httpx -silent -ports 80,443,3000,8080,8000,8081,8008,8888,8443,9000,9001,9090 | tee -a alive.txt

=============================================================

-->subfinder -d hackerone.com -all -o subdomains.txt
-->blind xss -> xsshunter.com enna site il ninum chyam
tools->subfinder(subdomain),,dirsearch(hiddenfiles)
-->parameter kandupidkan->paramspider,katana
-->subfinder -d tinder.com (ingane search chythamathi https:// idanda)
-->dirsearch -u https://hackerone.com  (ingane kodukam)  ithinte koode -i 301 enn koduthal aa status code varunath mathram enumerate chyum
-->
80
443
3000
8080
8000
8081
8008
8888
8443
9000
9001
9090

-->bugbounty il use chyavuna matoru tool aan nikto ->nikto -h [ip]
-->oru subdomain kitiyal ath burp ilek viduka enit avide ninum namuk ip kitum mukalil aayi.allengil ping,nslookup,whois oke chyumbol namuk ip kitum.so ee ip vech namuk nmap chyam 
-->nmap -A -v -p 80,443,8080,3000,8000,8888,8443,9000,9001,9090,1433,1434,3306 -T2 [ip]
-->ivide T2 ennu ittath slow aakan aan 
-->eth language aanen manasilayal aa languages in pothuvayi chela directories undakum so ath brute force chyth nokuka allengil manual aayi chyth nokuka
-->API bruteforce chyan ->ffuf -u tenet.htb/api/v1/FUZZ -w /usr/share/amass/wordlist/common.txt -fc 404
-->fc 404 ennal 404 varunath namuk avisham illan
-->ini site il ethengilum search bar il poi enhengilum type chyth search chyumbol url il kanam /?search=helo. ith repeater il itt test chyth response il nokumbol kanam ee hello ennath html il pala sthalathum save aakunund.so avide namal xss oke try chyanam ie `<hello>` enn iduka apol enth sambavikunu enn nokuka
-->ee /?search parameter maati vere enthengilum parameter namal thane indaki kodukuka like location= or token= enit athil enthengilum value ittit resposne il html il aa value save aakunundon nokuka angane save aakunundengil avide aan namuk xss polula bugs peten kandupidikan sadhyadha ullath karanam avide delevlopers filter onum chythitundakanamenila
-->oro button click chyumbozhum athinte action and js code nokanam.athinte html tag il name=something enna sathanam js code il engnae aaanen noknaam like js code il window.location.search enna kandal athinartahm search query parameter il ninumarn js aa parameter fetch chyunath apol namuk direct aayi aa parameter url idam mukalil token ennoke koduthath pole.so enit aa parameter il xss,sql i oke test chyam
-->sub3suite,Harpoon ee rand toolum namuk use chyan ith OSINT tools koodi aan
-->Sn1per,Photon ee tools um nokiko

=====================================================
-->Favicons are icons that serve as branding to your website. Each Favicon has some unique hash values which can be used to gather domains with the same hash function. Favicon hashes are simple to calculate. [FavFreak](https://github.com/devanshbatham/FavFreak) is one of the best tools which does this work for us
-->Command: cat urls.txt | python3 favfreak.py
-->Once the hash is calculated, you can use the same on internet search engines such as shodan to get the mass websites

VDP dork-> inurl : /responsible-disclosure/ reward
					inurl : /responsible-disclosure/ bounty
					inurl : /responsible-disclosure/ swag

-->namuk shodan vech ip scan chyam.bugbounty chyumbol ella site ilum namuk nmap chyan patila but shodan vech namuk scan chyan patum karanam shodan already ithoke scan chythirikunathan.so namuk terminalil ->shodan host [ip]  koduthal ethoke ports open aayikidakunund enariyan patum.

=====================================================

-->Known vulnerabilities ->https://github.com/projectdiscovery/nuclei-templates/tree/master/cves/2022 
-->updated wordlists -> https://github.com/swisskyrepo/PayloadsAllTheThingshttps://github.com/swisskyrepo/PayloadsAllTheThings
-->port scan -> Naabu(->naabu -host hackerone.com), Rustscan(->rustscan -a "reconftwips" -ulimit 10000 -r -1-65000)
-->nuclie enna tool use chyth known vuln kandupidikam like -> nuclei -t /Download/..wordlist . athayath namuk kitiya subdomains oke oru file il aaki vekanam enit aa file path -t kk shesham kodukanam.

