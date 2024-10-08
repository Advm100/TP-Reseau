# Rendu tp3
### I. ARP basics

```
PS C:\Windows\system32> ipconfig /all
Carte réseau sans fil Wi-Fi :

   Suffixe DNS propre à la connexion. . . :
   Description. . . . . . . . . . . . . . : Intel(R) Dual Band Wireless-N 7260
   Adresse physique . . . . . . . . . . . : 80-19-34-04-BA-B9
```
```
PS C:\Windows\system32> arp -a

Interface : 10.33.77.105 --- 0x8
  Adresse Internet      Adresse physique      Type
  10.33.79.254          7c-5a-1c-d3-d8-76     dynamique
  224.0.0.22            01-00-5e-00-00-16     statique
  224.0.0.251           01-00-5e-00-00-fb     statique
  224.0.0.252           01-00-5e-00-00-fc     statique
  239.255.255.250       01-00-5e-7f-ff-fa     statique
  255.255.255.255       ff-ff-ff-ff-ff-ff     statique

Interface : 192.168.56.1 --- 0x12
  Adresse Internet      Adresse physique      Type
  192.168.56.255        ff-ff-ff-ff-ff-ff     statique
  224.0.0.22            01-00-5e-00-00-16     statique
  224.0.0.251           01-00-5e-00-00-fb     statique
  224.0.0.252           01-00-5e-00-00-fc     statique
  230.0.0.1             01-00-5e-00-00-01     statique
  239.255.255.250       01-00-5e-7f-ff-fa     statique
```
```
Ip passerelle réseau de l'école : Passerelle par défaut: 10.33.79.254
Adresse MAC de la passerelle : 
  Adresse Internet      Adresse physique      Type
  10.33.79.254          7c-5a-1c-d3-d8-76     dynamique
```
```
PS C:\Windows\system32> arp -d 10.33.79.254
PS C:\Windows\system32> arp -a

Interface : 10.33.77.105 --- 0x8
  Adresse Internet      Adresse physique      Type
  10.33.65.63           44-af-28-c3-6a-9f     dynamique
  10.33.79.254          7c-5a-1c-d3-d8-76     dynamique
  10.33.79.255          ff-ff-ff-ff-ff-ff     statique
  224.0.0.22            01-00-5e-00-00-16     statique
  224.0.0.251           01-00-5e-00-00-fb     statique
  224.0.0.252           01-00-5e-00-00-fc     statique
  239.255.255.250       01-00-5e-7f-ff-fa     statique
  255.255.255.255       ff-ff-ff-ff-ff-ff     statique

Interface : 192.168.56.1 --- 0x12
  Adresse Internet      Adresse physique      Type
  192.168.56.255        ff-ff-ff-ff-ff-ff     statique
  224.0.0.22            01-00-5e-00-00-16     statique
  224.0.0.251           01-00-5e-00-00-fb     statique
  224.0.0.252           01-00-5e-00-00-fc     statique
  230.0.0.1             01-00-5e-00-00-01     statique
  239.255.255.250       01-00-5e-7f-ff-fa     statique
```
```
PS C:\Windows\system32> arp -d 10.33.79.254
PS C:\Windows\system32> arp -a

Interface : 192.168.56.1 --- 0x12
  Adresse Internet      Adresse physique      Type
  192.168.56.255        ff-ff-ff-ff-ff-ff     statique
  224.0.0.22            01-00-5e-00-00-16     statique
  224.0.0.251           01-00-5e-00-00-fb     statique
  224.0.0.252           01-00-5e-00-00-fc     statique
  230.0.0.1             01-00-5e-00-00-01     statique
  239.255.255.250       01-00-5e-7f-ff-fa     statique
```
# II. ARP dans un réseau local
### 1. Basics
```
PS C:\Windows\system32> ipconfig /all

Carte réseau sans fil Wi-Fi :
 Adresse physique . . . . . . . . . .:80-19-34-04-BA-B9
 Passerelle par défaut. . . . . . . . . : 172.20.10.1
 ```
 ```
 PS C:\Windows\system32> ipconfig /all

Carte réseau sans fil Wi-Fi :

   Suffixe DNS propre à la connexion. . . :
   Description. . . . . . . . . . . . . . : Intel(R) Dual Band Wireless-N 7260
   Adresse physique . . . . . . . . . . . : 80-19-34-04-BA-B9
   DHCP activé. . . . . . . . . . . . . . : Non
   Configuration automatique activée. . . : Oui
   Adresse IPv6 de liaison locale. . . . .: fe80::601b:504c:41c7:c671%8(préféré)
   Adresse IPv4. . . . . . . . . . . . . .: 172.20.10.3(préféré)
   Masque de sous-réseau. . . . . . . . . : 255.255.255.240
   Passerelle par défaut. . . . . . . . . :
   IAID DHCPv6 . . . . . . . . . . . : 125835572
   DUID de client DHCPv6. . . . . . . . : 00-01-00-01-29-5A-38-08-5C-B9-01-AE-9E-A1
   Serveurs DNS. . .  . . . . . . . . . . : fec0:0:0:ffff::1%1
                                       fec0:0:0:ffff::2%1
                                       fec0:0:0:ffff::3%1
   NetBIOS sur Tcpip. . . . . . . . . . . : Activé
```
```
   PS C:\Windows\system32> ping 172.20.10.6

Envoi d’une requête 'Ping'  172.20.10.6 avec 32 octets de données :
Réponse de 172.20.10.6 : octets=32 temps=5 ms TTL=128
Réponse de 172.20.10.6 : octets=32 temps=7 ms TTL=128
Réponse de 172.20.10.6 : octets=32 temps=5 ms TTL=128
Réponse de 172.20.10.6 : octets=32 temps=5 ms TTL=128

Statistiques Ping pour 172.20.10.6:
    Paquets : envoyés = 4, reçus = 4, perdus = 0 (perte 0%),
Durée approximative des boucles en millisecondes :
    Minimum = 5ms, Maximum = 7ms, Moyenne = 5ms
PS C:\Windows\system32> ping 172.20.10.4

Envoi d’une requête 'Ping'  172.20.10.4 avec 32 octets de données :
Réponse de 172.20.10.4 : octets=32 temps=99 ms TTL=128
Réponse de 172.20.10.4 : octets=32 temps=79 ms TTL=128
Réponse de 172.20.10.4 : octets=32 temps=85 ms TTL=128
Réponse de 172.20.10.4 : octets=32 temps=100 ms TTL=128

Statistiques Ping pour 172.20.10.4:
    Paquets : envoyés = 4, reçus = 4, perdus = 0 (perte 0%),
Durée approximative des boucles en millisecondes :
    Minimum = 79ms, Maximum = 100ms, Moyenne = 90ms
```
# 2. ARP
```
PS C:\Windows\system32> arp -a

Interface : 172.20.10.3 --- 0x8
  Adresse Internet      Adresse physique      Type
  172.20.10.4           1c-ce-51-24-c7-33     dynamique
  172.20.10.6           9c-b6-d0-05-18-db     dynamique
  172.20.10.15          ff-ff-ff-ff-ff-ff     statique
  224.0.0.22            01-00-5e-00-00-16     statique
  224.0.0.251           01-00-5e-00-00-fb     statique
  239.255.102.18        01-00-5e-7f-66-12     statique
  239.255.255.250       01-00-5e-7f-ff-fa     statique

Interface : 192.168.56.1 --- 0x12
  Adresse Internet      Adresse physique      Type
  192.168.56.255        ff-ff-ff-ff-ff-ff     statique
  224.0.0.22            01-00-5e-00-00-16     statique
  224.0.0.251           01-00-5e-00-00-fb     statique
  224.0.0.252           01-00-5e-00-00-fc     statique
  230.0.0.1             01-00-5e-00-00-01     statique
  239.255.255.250       01-00-5e-7f-ff-fa     statique
```