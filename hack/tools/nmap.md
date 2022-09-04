-->nmap -sS   -T4   -p- [ip]                   --(tcp synscan)

-->enabling fast mode  -->nmap -sV -F -O [ip]
-->aggressive scan to reveal all details -->nmap -A [ip]
-->service detection scan with script engine -->nmap -sC -sV [ip]
-->udp scan with aggresive speed -->nmap -sU -T4 [ip]
-->stealth and slow scan to evade firewalls -->nmap -sS -T1 -f [ip]
-->null scan to evade firewalls and IDS -->nmap -sN -T1 [ip]
-->fin scan to evade firewall and IDS -->nmap -FN -T1 [ip]
-->decoy scan to evade firewall and IDS -->nmap -D ip1,ip2,yourip [ip]
-->changing useragent for firewall and IDS -->nmap -sV --script-args http.useragent= "useragenthere" ip

-->-A,-sV,regular nikto scan, scripting engine okke use chythal IDS,firewall oke detect chyum


### nikto
-->scaning a webapp for vulnerabilities -->nikto -h [ip]
-->scanning for vuln and disabling ssl -->nikto -h [ip] -nossl
     This opion is useful for sites that dont force secure transport to https
-->scanning for vuln with ssl -->nikto -h [ip] -ssl
     if the site forces transport using tls/ssl.athayath site ssl vazhi mathrame transportation nadaknulu engil ith use chyathe nivarthi ila
	 
#### nikto plugins:
plugins use chythal kooduthal vulnerabilities kandethanayekum
-->plugins nokan -->nikto --list-plugins
      plugins theranjeduthal aa name specifu chuyanam:
      -->nikto -h [target ip] -Plugins [plugin-name]