home directory-->cd ~

-->finding the firefox history data(sqlite)-->     
`cd  C:\Users\jmich\AppData\Roaming\Mozilla\Firefox\Profiles\avxcu01g.default-release`

> cd C:\Users\jmich\AppData\Roaming\Mozilla\Firefox\Profiles\avxcu01g.default-releas>      $db="C:\Users\jmich\AppData\Roaming\Mozilla\Firefox\Profiles\avxcu01g.default-release\places.sqlite"
> invoke-sqlitequery -datasource $db -query "PRAGMA STATS"
> invoke-sqlitequery -datasource $db -query "SELECT * FROM moz_places"
     ivide moz_places enna table il ninum datas dump chyunu
> invoke-sqlitequery -datasource $db -query "SELECT url FROM moz_places"
   note-->ee places.sqlite ennath oru database aan.ithupole kure databases und.key4.db enna database il aan passwords okke store chyunath.firefoxil mathramalla mattu browsersilum ithupole und.


# To create a new file :
->`New-Item C:\Users\jmich\Desktop\celo\ -Name "power.js"`
new-item enathan command. athin shesham path kodukanam athinu sehsnam file name with extension koduthal aayi ok

-->New-Item cmdlet is used to create a text file and Set-Content cmdlet to put content into it.