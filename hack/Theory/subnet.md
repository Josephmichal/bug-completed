# Start with an example
-->oru subnet vech namuk athinte subnet mask kandupidikan patum, ethra network undakam enn manasilakan patum, aa oro networkilum ethra ip adress assign chyan patumen manasilkan patum, athupole aa oro networkilum ethra host assign chyan patumenum namuk manasilkan patum
-->EG : 192.168.10.0/28   ithan subnet

192 means it is a class c ip adress.the default subnet of class c is `255.255.255.0` . This is because there are by default there are 24 bits reserved for the network and 8 bits reserved for the hosts.so once you calculate each bits on this blok we will get 255.255.255.0.

Here the CIDR value is /28 and we know the number of network bits on class subnet is `24` . so we need to borrow 4 bits from host to make it `28`.so the new subnet mask we will get is `255.255.255.240`. 240 engane kity ennal 4 bits borrow chythath calculate chythal kitum ie, `2^7+2^6+2^5+2^4=240`.  subnet mask il 2^7 muthal 2^0 vere bits undakum.so namal 192.168.10.0/28   inte subnet mask kandupidichu.

ini namuk ethra number of network ithil undakum enn kandupidikam.so to find the number of network, we have a formula called `2^n` (here n indicates the total no.of bits borrowed from host) so namuk ariyam namal host il ninum 4 bits borrow chythitund so,  total number of network is 2^n ie, 2^4=16.so we can create 16 networks with this ip 192.168.10.0/28. 

ini oro networkilum ethra ip address undakam enn kandupidikam.To find the no.of ip address on each network we have a formula called `2^n` (here n indicates the total no.of remaining host bits) so namuk ariyam 4 bits already eduthu so ini baki ullath 4 bits aan so 2^n ie, 2^4 = 16. so we can create 16 no.of ip address on each network

ini namuk oro network ilum ethra host undakam enn kandupidikam.To find the total no.of hosts on each network we have a formula called `12^n - 2` (here n indicates the toatal no.of remaining hosts bits and 2 means on each netwrok the first address is reserved for the `network ID` and the las ip is a `broadcast ID` ).so namukariyam baki 4 host bits aan ullath so 2^n - 2 is 2^4 - 2 = 14. so we can create 14 host ip address on each network

so Total no.of Networks ->16
    Total no.of Hosts ->16

`````````````````````
Network   Network id          Host ip address             Broadcast address
	1    192.168.10.0     192.168.10.1-192.168.10.14        192.168.10.15
	2    192.168.10.16    192.168.10.17-192.168.10.30       192.168.10.31
	3    192.168.10.32    192.168.10.33-192.168.10.46       192.168.10.47
	4    192.168.10.48    192.168.10.49-192.168.10.62       192.168.10.63
	5    192.168.10.64    192.168.10.65-192.168.10.78       192.168.10.79
	.... ingane last 
	15   192.168.10.224   192.168.10.225-192.168.10.238     192.168.10.239
	16   192.168.10.240   192.168.10.241-192.168.10.254     192.168.10.255
`````````````````````

so namal calculate chyumbol ingane aan each network and its ip adress ok

==========================================================

## THEORY 
WHAT IS SUBNETTING ?
-->Dividing a large network into multiple small networks is called Subnetting

Now lets look at the different classes and its ip addresses

Class A (CIDR value = /8)
Ip Adress = 1-126
Default Subnet Mask = 255.0.0.0
Here 8 bits are reserved for the network and remaining 24 bits are reserved for host ie,

```
Network Bits                          Host Bits
     8                                   24
  11111111           00000000  00000000  00000000  00000000
```

WHAT IS A CIDR VALUE ?
-->It stands for classless inter domain routing.It is the total number of Network Bits.so ivide  /8 enna CIDR varumbol 8 network bits aan undavuka

Class B (CIDR value = /16)
Ip Adress = 128-191
Default Subnet Mask = 255.255.0.0
Here 16 bits are reserved for the network and remaining 16 bits are reserved for host ie,

```
      Network Bits                           Host Bits
           16                                   16
  11111111  11111111                     00000000  00000000
````

Class C (CIDR value = /24)
Ip Adress = 192-223
Default Subnet Mask = 255.255.255.0
Here 24 bits are reserved for the network and remaining 8 bits are reserved for host ie,

```
        Network Bits                             Host Bits
             24                                      8
  11111111  11111111 11111111                    00000000
```

NOW LETS HAVE AN EXAMPLE -> 192.168.10.0/24
-->so first 192 , it means its a class C ip address.so its default subnet mask is 255.255.255.0 . ith enganeyan verunath enn manasilakanengil ip4 pati ariyanam. ie, ip version 4 is a 32 bit adress and it is differed into 4 blocks of 8 bits ie,

```
     255               255                255                 255
   8 bits             8 bits            8 bits               8 bits
   block 1           block 2           block 3              block 4
```
 WHERE NUMBER - 1 INDICATES NETWORK BITS AND NUMBER - 2 INDICATES HOST BITS

```
   255               255                255                 255
  11111111        11111111            11111111             00000000
   block 1           block 2           block 3              block 4
```

oro bits inum athintethaya corresponding 2^ und.bits count chyunath right to left aan ie, <-- (valathun idathotek). so angane verumbol

```
    2^7 2^6 2^5 2^4 2^3 2^2 2^1 2^0
     1   1   1   1   1   1   1   1
```

ithupole oro bitinum 2^ und.ath network aayalum host aayalum. so ee 2^0 muthal 2^7 vere add chythal namuk 255 kitum.so class C ile oro block um add chythal namuk 255.255.255.0 enn kitum. ivide 0 vannath host bit add chyth kitiyathan.namuk network bits mathram add chythal mathrame subnet kitu karanm host bits are always zero.

LETS HAVE ANOTHER EXAMPLE -> 192.168.10.0/25
-->Here the ip starts from 192 so its a class C ip address.The dufault subnet is 255.255.255.0 . But here we can see the CIDR value is /25. it means there must be 25 network bits on the subnet.So to make 25 bits we need to borrow one bit from the host. After borrowing one host the new subnet mask is 255.255.255.128 ie,

```
       Network Bits                             Host Bits
             24                                      8
  11111111  11111111 11111111                    10000000
```

ivide host part il nokiyal kanam aadyathe bits mathram one aan.athayath aa one bit borrow chythal /25 namal aakunath. aa one bits inte value ennath 2^7 aan. 2^7 ennal 128 aan. ini ethra network unden kandupidkam

HOW TO FIND THE NUMBER OF NETWORK ?
-->To find the number of network of this ip adress(192.168.10.0/25), we have a formula ie, `2^n` . Here n indicates the total number of bits borrowed from host.Hence we borrowed only one bit, so 2^1 = 2. so we can create two networks with this ip address

HOW TO FIND THE NUMBER OF IP ADDRESS ON EACH NETWORK ?
-->To find the number of ip address on each network we have a formula ie, `2^n` . Here n is the total number of host bits remaining. so 2^7 = 128. so we can create 128 ip address on each network

HOW TO FIND THE NUMBER OF HOST ON EACH NETWORK ?
-->REMEMBER -> Number of Host means total number of ip address we can assign on each devices on the network. To find the total number of host on each network we have a formula ie, `2^n - 2` . Here n indicates the total number of remaining host bits.Here 2 means on every network the first ip adress is reserved for the network id and the last ip adress is reserved for the broadcast id.so baki varuna ip adresses mathrame namuk oro devices ilum assign chyan patu. so 2^7 - 2 = 126. So we will have total 126 host ip address on each network. mukalile start with an example il oro networkilum ip adress varunathoke kanikunund nokiko.