# Bonus : DHCP spoofing
### 2. DHCP spoofing
```
adam@adam-ubuntu:~$ sudo apt-get install dnsmasq
[sudo] password for adam:
Reading package lists... Done
Building dependency tree... Done
Reading state information... Done
dnsmasq is already the newest version (2.90-2build2).
0 upgraded, 0 newly installed, 0 to remove and 39 not upgraded.
adam@adam-ubuntu:~$ sudo nano /etc/dnsmasq.conf
```
On ajoute ça 
```
# Définir la passerelle avec l'option 3
dhcp-option=3,10.5.1.254

# vrai dns par exemple 1.1.1.1
dhcp-option=6,1.1.1.1

# range de .240 a .250
dhcp-range=10.5.1.240,10.5.1.250,12h
```
