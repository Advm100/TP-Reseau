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
