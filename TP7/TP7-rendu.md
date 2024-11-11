# TP7 : On dit chiffrer pas crypter
# II. Serveur Web
### 1. HTTP
### B. Configuration
```
[adam@web nginx]$ sudo ss -lnpt | grep 80
LISTEN 0      511          0.0.0.0:80        0.0.0.0:*    users:(("nginx",pid=14074,fd=6),("nginx",pid=14073,fd=6))
LISTEN 0      511             [::]:80           [::]:*    users:(("nginx",pid=14074,fd=7),("nginx",pid=14073,fd=7))
```
```
[adam@web ~]$ sudo firewall-cmd --list-ports
[sudo] password for adam:
80/tcp
```
### C. Tests client
```
[adam@client ~]$ ping sitedefou.tp7.b1
PING sitedefou.tp7.b1 (10.7.1.11) 56(84) bytes of data.
64 bytes from sitedefou.tp7.b1 (10.7.1.11): icmp_seq=1 ttl=64 time=1.43 ms
64 bytes from sitedefou.tp7.b1 (10.7.1.11): icmp_seq=2 ttl=64 time=2.13 ms
64 bytes from sitedefou.tp7.b1 (10.7.1.11): icmp_seq=3 ttl=64 time=2.17 ms
^C
--- sitedefou.tp7.b1 ping statistics ---
3 packets transmitted, 3 received, 0% packet loss, time 2007ms
rtt min/avg/max/mdev = 1.434/1.912/2.170/0.338 ms
```

Voici les premières ligne du HTML de mon site de fou :
```
[adam@client ~]$ curl http://sitedefou.tp7.b1
<!doctype html>
<html>
  <head>
    <meta charset='utf-8'>
    <meta name='viewport' content='width=device-width, initial-scale=1'>
    <title>HTTP Server Test Page powered by: Rocky Linux</title>
    <style type="text/css">
      /*<![CDATA[*/
```
### D. Analyze
```
Voir tcp_http.pcap
J'avais un pbm sur Wireshark que je n'ai pas réussi a régler dcp je l'ai fais avec tcpdump pour rendre quelque chose de ressemblant.
```
```
State             Recv-Q            Send-Q                       Local Address:Port                        Peer Address:Port             Process
LISTEN            0                 128                                0.0.0.0:ssh                              0.0.0.0:*
LISTEN            0                 511                                0.0.0.0:http                             0.0.0.0:*
ESTAB             0                 0                               10.7.1.101:ssh                             10.7.1.1:52677
ESTAB             0                 0                               10.7.1.11:http                             10.7.1.11:80
LISTEN            0                 128                                   [::]:ssh                                 [::]:*
LISTEN            0                 511                                   [::]:http                                [::]:*
```
### 2. On rajoute un S
### A. Config
```
[adam@web /]$ sudo ss -lnpt | grep nginx
LISTEN 0      511          0.0.0.0:443       0.0.0.0:*    users:(("nginx",pid=12137,fd=6),("nginx",pid=12136,fd=6))
LISTEN 0      511          0.0.0.0:80        0.0.0.0:*    users:(("nginx",pid=12137,fd=7),("nginx",pid=12136,fd=7))
LISTEN 0      511             [::]:443          [::]:*    users:(("nginx",pid=12137,fd=9),("nginx",pid=12136,fd=9))
LISTEN 0      511             [::]:80           [::]:*    users:(("nginx",pid=12137,fd=8),("nginx",pid=12136,fd=8))
```
```
[adam@web /]$ sudo firewall-cmd --list-ports
443/tcp
```
### B. Test test test analyyyze
```
Problème avec Wireshark pour l'instant, j'essaye de trouver le pbm
```
# III. Serveur VPN
### 1. Install et conf Wireguard
```
4: wg0: <POINTOPOINT,NOARP,UP,LOWER_UP> mtu 1420 qdisc noqueue state UNKNOWN group default qlen 1000
    link/none
    inet 10.7.200.1/24 scope global wg0
       valid_lft forever preferred_lft forever
```
```
[adam@vpn network-scripts]$ sudo ss -tuln | grep ':51820'
udp   UNCONN 0      0            0.0.0.0:51820      0.0.0.0:*
udp   UNCONN 0      0               [::]:51820         [::]:**
```
### 3. Proofs
```
[adam@client ~]$ ping 10.7.200.1
PING 10.7.200.1 (10.7.200.1) 56(84) bytes of data.
64 bytes from 10.7.200.1: icmp_seq=1 ttl=64 time=5.03 ms
64 bytes from 10.7.200.1: icmp_seq=2 ttl=64 time=2.99 ms
64 bytes from 10.7.200.1: icmp_seq=3 ttl=64 time=4.24 ms
^C
--- 10.7.200.1 ping statistics ---
3 packets transmitted, 3 received, 0% packet loss, time 2005ms
rtt min/avg/max/mdev = 2.989/4.083/5.026/0.838 ms
```
Voir ping1_vpn et ping2_vpn

