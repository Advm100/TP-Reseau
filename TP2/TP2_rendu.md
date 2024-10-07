# Rendu TP1
# I. Simplest LAN
### 1. Quelques pings


```
PS C:\Windows\system32> Get-NetIPAddress -InterfaceAlias "Ethernet"

IPAddress         : fe80::3528:735d:5062:8f4c%17
InterfaceIndex    : 17
InterfaceAlias    : Ethernet
AddressFamily     : IPv6
Type              : Unicast
PrefixLength      : 64
PrefixOrigin      : WellKnown
SuffixOrigin      : Link
AddressState      : Deprecated
ValidLifetime     : Infinite ([TimeSpan]::MaxValue)
PreferredLifetime : Infinite ([TimeSpan]::MaxValue)
SkipAsSource      : False
PolicyStore       : ActiveStore

IPAddress         : 169.254.156.245
InterfaceIndex    : 17
InterfaceAlias    : Ethernet
AddressFamily     : IPv4
Type              : Unicast
PrefixLength      : 16
PrefixOrigin      : WellKnown
SuffixOrigin      : Link
AddressState      : Tentative
ValidLifetime     : Infinite ([TimeSpan]::MaxValue)
PreferredLifetime : Infinite ([TimeSpan]::MaxValue)
SkipAsSource      : False
PolicyStore       : ActiveStore

IPAddress         : 10.42.15.2
InterfaceIndex    : 17
InterfaceAlias    : Ethernet
AddressFamily     : IPv4
Type              : Unicast
PrefixLength      : 24
PrefixOrigin      : Manual
SuffixOrigin      : Manual
AddressState      : Tentative
ValidLifetime     : Infinite ([TimeSpan]::MaxValue)
PreferredLifetime : Infinite ([TimeSpan]::MaxValue)
SkipAsSource      : False
PolicyStore       : ActiveStore

adam@adam-ubuntu:~$ ip addr show enp0s8
3: enp0s8: <BROADCAST,MULTICAST,UP,LOWER_UP> mtu 1500 qdisc fq_codel state UP group default qlen 1000
    link/ether 08:00:27:4d:01:20 brd ff:ff:ff:ff:ff:ff
    inet 192.168.56.101/24 brd 192.168.56.255 scope global dynamic noprefixroute enp0s8
       valid_lft 477sec preferred_lft 477sec
    inet6 fe80::51b7:1811:55a:c0d5/64 scope link noprefixroute
       valid_lft forever preferred_lft forever
```   

```
adam@adam-ubuntu:~$ Envoi d’une requête 'Ping'  192.168.56.1 avec 32 octets de données :
temps<1ms TTL=128
Réponse de 192.168.56.1 : octets=32 temps<1ms TTL=128
Réponse de 192.168.56.1 : octets=32 temps<1ms TTL=128
Réponse de 192.168.56.1 : octets=32 temps<1ms TTL=128

Statistiques Ping pour 192.168.56.1:
    Paquets : envoyés = 4, reçus = 4, perdus = 0 (perte 0%),
Durée approximative des boucles en millisecondes :
    Minimum = 0ms, Maximum = 0ms, Moyenne = 0msEnvoi: command not found
	
PS C:\Windows\system32> ping 192.168.56.101

Envoi d’une requête 'Ping'  192.168.56.101 avec 32 octets de données :
Réponse de 192.168.56.101 : octets=32 temps<1ms TTL=64
Réponse de 192.168.56.101 : octets=32 temps<1ms TTL=64
Réponse de 192.168.56.101 : octets=32 temps<1ms TTL=64
Réponse de 192.168.56.101 : octets=32 temps<1ms TTL=64

Statistiques Ping pour 192.168.56.101:
    Paquets : envoyés = 4, reçus = 4, perdus = 0 (perte 0%),
Durée approximative des boucles en millisecondes :
    Minimum = 0ms, Maximum = 0ms, Moyenne = 0ms

```
# II. Utilisation des ports
### 1. Animal numérique
```
PS C:\netcat-1.11> ./nc.exe -l -p 9999
>>
```
```
PS C:\Windows\system32> netstat -a -b -n
	 [AnyDesk.exe]
  TCP    0.0.0.0:9999           0.0.0.0:0              LISTENING
```
```
PS C:\netcat-1.11> .\nc64.exe -l -p 9999
allo

adam@adam-ubuntu:~$ nc 192.168.56.1 9999
allo
```
```
PS C:\Windows\system32> netstat -anb | Select-String 9999 -Context 0,1

>   TCP    0.0.0.0:9999           0.0.0.0:0              LISTENING
   [nc64.exe]
   
adam@adam-ubuntu:~$ sudo ss -tnp
State       Recv-Q       Send-Q                       Local Address:Port                       Peer Address:Port        Process
ESTAB       0            0                           192.168.56.101:48132                      192.168.56.1:9999         users:(("nc",pid=5613,fd=3))
```
```
adam@adam-ubuntu:~$ nc -l -p 9999
hello

PS C:\netcat-1.11> .\nc64.exe 192.168.56.101 9999
hello

sudo ss -tnp
[sudo] password for adam:
State       Recv-Q       Send-Q                       Local Address:Port                       Peer Address:Port        Process
ESTAB       0            0                           192.168.56.101:9999                       192.168.56.1:37394        users:(("nc",pid=5721,fd=4))
```
```
PS C:\Windows\system32> netstat -anb | Select-String 9999 -Context 0,1

>   TCP    192.168.56.1:37394     192.168.56.101:9999    ESTABLISHED
   [nc64.exe]
```

# III. Analyse de vos applications usuelles
### 2. Autres services
```
udp        0      0 0.0.0.0:35871           0.0.0.0:*                           5033/firefox
udp        0      0 0.0.0.0:60916           0.0.0.0:*                           5033/firefox
udp        0      0 0.0.0.0:36761           0.0.0.0:*                           5033/firefox

udp        0      0 224.0.0.251:5353        0.0.0.0:*                           6801/chrome
udp        0      0 224.0.0.251:5353        0.0.0.0:*                           6801/chrome
```
