# Rendu TP1:


### I. Récolte infos

```
PS C:\Users\Adam> ipconfig
Carte réseau sans fil Wi-Fi :

   Suffixe DNS propre à la connexion. . . :
   Adresse IPv6 de liaison locale. . . . .: fe80::601b:504c:41c7:c671%8
   Adresse IPv4. . . . . . . . . . . . . .: 10.33.77.105
   Masque de sous-réseau. . . . . . . . . : 255.255.240.0
   Passerelle par défaut. . . . . . . . . : 10.33.79.254

Carte Ethernet Ethernet 2 :

   Suffixe DNS propre à la connexion. . . :
   Adresse IPv6 de liaison locale. . . . .: fe80::40aa:8483:1abf:dfe9%18
   Adresse IPv4. . . . . . . . . . . . . .: 192.168.56.1
   Masque de sous-réseau. . . . . . . . . : 255.255.255.0
   Passerelle par défaut. . . . . . . . . :

```
```
PS C:\Users\Adam> ipconfig /all
Carte réseau sans fil Wi-Fi :

   Suffixe DNS propre à la connexion. . . :
   Description. . . . . . . . . . . . . . : Intel(R) Dual Band Wireless-N 7260
   Adresse physique . . . . . . . . . . . : 80-19-34-04-BA-B9
   DHCP activé. . . . . . . . . . . . . . : Oui
   Configuration automatique activée. . . : Oui
   Adresse IPv6 de liaison locale. . . . .: fe80::601b:504c:41c7:c671%8(préféré)
   Adresse IPv4. . . . . . . . . . . . . .: 10.33.77.105(préféré)
   Masque de sous-réseau. . . . . . . . . : 255.255.240.0
   Bail obtenu. . . . . . . . . . . . . . : jeudi 26 septembre 2024 17:43:31
   Bail expirant. . . . . . . . . . . . . : samedi 28 septembre 2024 14:06:55
   Passerelle par défaut. . . . . . . . . : 10.33.79.254
   Serveur DHCP . . . . . . . . . . . . . : 10.33.79.254
   IAID DHCPv6 . . . . . . . . . . . : 125835572
   DUID de client DHCPv6. . . . . . . . : 00-01-00-01-29-5A-38-08-5C-B9-01-AE-9E-A1
   Serveurs DNS. . .  . . . . . . . . . . : 8.8.8.8
                                       1.1.1.1
   NetBIOS sur Tcpip. . . . . . . . . . . : Activé
   ```
   Bonus:
   ```
   PS C:\Users\Adam> Get-Service -Name MpsSvc

Status   Name               DisplayName
------   ----               -----------
Running  MpsSvc             Pare-feu Windows Defender
```
```
```
### 2. Utiliser le réseau 

```
 PS C:\Users\Adam> Ping 10.33.77.105

Envoi d’une requête 'Ping'  10.33.77.105 avec 32 octets de données :
Réponse de 10.33.77.105 : octets=32 temps<1ms TTL=128
Réponse de 10.33.77.105 : octets=32 temps<1ms TTL=128
Réponse de 10.33.77.105 : octets=32 temps<1ms TTL=128
Réponse de 10.33.77.105 : octets=32 temps<1ms TTL=128

Statistiques Ping pour 10.33.77.105:
    Paquets : envoyés = 4, reçus = 4, perdus = 0 (perte 0%),
Durée approximative des boucles en millisecondes :
    Minimum = 0ms, Maximum = 0ms, Moyenne = 0ms
```
```

PS C:\Users\Adam> ping 127.0.0.1

Envoi d’une requête 'Ping'  127.0.0.1 avec 32 octets de données :
Réponse de 127.0.0.1 : octets=32 temps<1ms TTL=128
Réponse de 127.0.0.1 : octets=32 temps<1ms TTL=128
Réponse de 127.0.0.1 : octets=32 temps<1ms TTL=128
Réponse de 127.0.0.1 : octets=32 temps<1ms TTL=128

Statistiques Ping pour 127.0.0.1:
    Paquets : envoyés = 4, reçus = 4, perdus = 0 (perte 0%),
Durée approximative des boucles en millisecondes :
    Minimum = 0ms, Maximum = 0ms, Moyenne = 0ms
```
```
Envoi d’une requête 'Ping'  10.33.79.254 avec 32 octets de données :
Délai d’attente de la demande dépassé.
Délai d’attente de la demande dépassé.
Délai d’attente de la demande dépassé.
Délai d’attente de la demande dépassé.

Statistiques Ping pour 10.33.79.254:
    Paquets : envoyés = 4, reçus = 0, perdus = 4 (perte 100%),
```
```
PS C:\Users\Adam> Ping 10.33.66.78

Envoi d’une requête 'Ping'  10.33.66.78 avec 32 octets de données :
Réponse de 10.33.66.78 : octets=32 temps=3 ms TTL=64
Réponse de 10.33.66.78 : octets=32 temps=108 ms TTL=64
Réponse de 10.33.66.78 : octets=32 temps=13 ms TTL=64
Réponse de 10.33.66.78 : octets=32 temps=3 ms TTL=64

Statistiques Ping pour 10.33.66.78:
    Paquets : envoyés = 4, reçus = 4, perdus = 0 (perte 0%),
Durée approximative des boucles en millisecondes :
    Minimum = 3ms, Maximum = 108ms, Moyenne = 31ms
```
```
PS C:\Users\Adam> Ping www.riot.com

Envoi d’une requête 'ping' sur e7072.e12.akamaiedge.net [23.51.111.109] avec 32 octets de données :
Réponse de 23.51.111.109 : octets=32 temps=10 ms TTL=55
Réponse de 23.51.111.109 : octets=32 temps=10 ms TTL=55
Réponse de 23.51.111.109 : octets=32 temps=10 ms TTL=55
Réponse de 23.51.111.109 : octets=32 temps=10 ms TTL=55

Statistiques Ping pour 23.51.111.109:
    Paquets : envoyés = 4, reçus = 4, perdus = 0 (perte 0%),
Durée approximative des boucles en millisecondes :
    Minimum = 10ms, Maximum = 10ms, Moyenne = 10ms
```
```
PS C:\Users\Adam> nslookup www.thinkerview.com
Serveur :   dns.google
Address:  8.8.8.8

Réponse ne faisant pas autorité :
Nom :    www.thinkerview.com
Addresses:  2a06:98c1:3121::7
          2a06:98c1:3120::7
          188.114.96.7
          188.114.97.7

PS C:\Users\Adam> nslookup www.wikileaks.org
Serveur :   dns.google
Address:  8.8.8.8

Réponse ne faisant pas autorité :
Nom :    wikileaks.org
Addresses:  80.81.248.21
          51.159.197.136
Aliases:  www.wikileaks.org

PS C:\Users\Adam> nslookup  www.torproject.org
Serveur :   dns.google
Address:  8.8.8.8

Réponse ne faisant pas autorité :
Nom :    www.torproject.org
Addresses:  2620:7:6002:0:466:39ff:fe7f:1826
          2620:7:6002:0:466:39ff:fe32:e3dd
          2a01:4f9:c010:19eb::1
          2a01:4f8:fff0:4f:266:37ff:feae:3bbc
          2a01:4f8:fff0:4f:266:37ff:fe2c:5d19
          95.216.163.36
          116.202.120.165
          204.8.99.146
          116.202.120.166
          204.8.99.144
```
```
```

### 4.Network scanning et adresses IP
```
PS C:\Users\Adam> nmap -sn -PR 10.33.64.0/20

Nmap scan report for 10.33.66.78
Host is up (0.042s latency).
MAC Address: E4:B3:18:48:36:68 (Intel Corporate)
Nmap scan report for 10.33.67.113
Host is up (0.16s latency).
MAC Address: D2:91:DE:DF:9A:6E (Unknown)
Nmap scan report for 10.33.69.68
Host is up (0.27s latency).
MAC Address: EE:E8:D9:89:3F:F1 (Unknown)
Nmap scan report for 10.33.69.82
Host is up (0.53s latency).
MAC Address: 50:A6:D8:A9:55:02 (Apple)
```
```

### Changer d'adresse IP

PS C:\Users\Adam> ip config
```
```
Carte réseau sans fil Wi-Fi :

   Suffixe DNS propre à la connexion. . . :
   Adresse IPv6 de liaison locale. . . . .: fe80::5cd2:c981:10b1:5928%19
   Adresse IPv4. . . . . . . . . . . . . .: 10.33.70.238
   Masque de sous-réseau. . . . . . . . . : 255.255.240.0
   Passerelle par défaut. . . . . . . . . : 10.33.79.254
```