1) Directory search
-->gobuster dir -u http://[ip]:port(if necessary) -w /usr/share/amass/wordlists/rockyou.txt 2> /dev/null
-->gobuster dir -u http://[ip]:port(if necessary) -w /usr/share/amass/wordlists/rockyou.txt 2> /dev/null --wildcard         (error varunengil --wildcard use chyth search chyy)


--------------------------------------------------------------------
2) WordPress scan
-->wpscan --url http://internal.thm -e vp,u 
       vp- vulnerable plugins, u- users , -e - enumerate
		ee scan chythapoo admin enna usernames kandu so:
-->wpscan --url http://internal.thm/blog --usernames admin --passwords /usr/share/amass/wordlists/rockyou.txt

----------------------------------------------------------------
3) rdp
-->xfreerdp /u:admin /p:password /cert:ignore /v:MACHINE_IP /workarea

-----------------------------------------------------------------
4)sftp (transfer large files)
