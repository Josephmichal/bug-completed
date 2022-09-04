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

tools->subfinder(subdomain),,dirsearch(hiddenfiles)

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