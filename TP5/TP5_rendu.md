# TP5 : Un ptit LAN à nous
### I. Setup
```
2: enp0s3: <BROADCAST,MULTICAST,UP,LOWER_UP> mtu 1500 qdisc fq_codel state UP group default qlen 1000
    link/ether 08:00:27:8c:dd:13 brd ff:ff:ff:ff:ff:ff
    inet 10.5.1.11/24 brd 10.5.1.255 scope global enp0s3
       valid_lft forever preferred_lft forever
    inet 192.168.56.103/24 metric 100 brd 192.168.56.255 scope global dynamic enp0s3
       valid_lft 356sec preferred_lft 356sec
    inet6 fe80::a00:27ff:fe8c:dd13/64 scope link 
       valid_lft forever preferred_lft forever
```
```
adam@adam-ubuntu:~/Desktop$ sudo hostnamectl
 Static hostname: Dobrazil
       Icon name: computer-vm
         Chassis: vm 🖴
```
```
2: enp0s3: <BROADCAST,MULTICAST,UP,LOWER_UP> mtu 1500 qdisc fq_codel state UP group default qlen 1000
    link/ether 08:00:27:6e:7c:3f brd ff:ff:ff:ff:ff:ff
    inet 10.1.1.12/24 brd 10.1.1.255 scope global enp0s3
       valid_lft forever preferred_lft forever
    inet6 fe80::cd05:cc5b:89ed:a31a/64 scope link 
       valid_lft forever preferred_lft forever
```
```
adam@adam-ubuntu:~/Desktop$ sudo hostnamectl
 Static hostname: Dobranaw
       Icon name: computer-vm
         Chassis: vm 🖴
```
```
[adam@localhost ~]$ ip a
2: enp0s3: <BROADCAST,MULTICAST,UP,LOWER_UP> mtu 1500 qdisc fq_codel state UP group default qlen 1000
    link/ether 08:00:27:62:ae:04 brd ff:ff:ff:ff:ff:ff
    inet 10.5.1.254/24 brd 10.5.1.255 scope global noprefixroute enp0s3
       valid_lft forever preferred_lft forever
    inet6 fe80::a00:27ff:fe62:ae04/64 scope link
```
```
[adam@localhost ~]$ sudo hostnamectl
 Static hostname: Brazilia
       Icon name: computer-vm
         Chassis: vm 🖴
      Machine ID: 194f28cd34194bfe8a3e25c17664dd18
         Boot ID: 4ab7c54985254a62a21aa76f01a47629
  Virtualization: oracle
Operating System: Rocky Linux 9.4 (Blue Onyx)
     CPE OS Name: cpe:/o:rocky:rocky:9::baseos
          Kernel: Linux 5.14.0-427.13.1.el9_4.x86_64
    Architecture: x86-64
 Hardware Vendor: innotek GmbH
  Hardware Model: VirtualBox
Firmware Version: VirtualBox
```
```
[adam@localhost ~]$ ping 10.5.1.11
PING 10.5.1.11 (10.5.1.11) 56(84) bytes of data.
64 bytes from 10.5.1.11: icmp_seq=1 ttl=64 time=6.14 ms
64 bytes from 10.5.1.11: icmp_seq=2 ttl=64 time=2.73 ms
64 bytes from 10.5.1.11: icmp_seq=3 ttl=64 time=2.82 ms
64 bytes from 10.5.1.11: icmp_seq=4 ttl=64 time=2.98 ms
64 bytes from 10.5.1.11: icmp_seq=5 ttl=64 time=3.18 ms
64 bytes from 10.5.1.11: icmp_seq=6 ttl=64 time=2.02 ms
64 bytes from 10.5.1.11: icmp_seq=7 ttl=64 time=2.48 ms
64 bytes from 10.5.1.11: icmp_seq=8 ttl=64 time=2.53 ms
^C
--- 10.5.1.11 ping statistics ---
8 packets transmitted, 8 received, 0% packet loss, time 7019ms
rtt min/avg/max/mdev = 2.018/3.109/6.135/1.189 ms
```
### II. Accès internet pour tous
### 1. Accès internet routeur
```
PING ynov.com (172.67.74.226) 56(84) bytes of data.
64 bytes from 172.67.74.226 (172.67.74.226): icmp_seq=1 ttl=53 time=39.0 ms
64 bytes from 172.67.74.226 (172.67.74.226): icmp_seq=2 ttl=53 time=113 ms
64 bytes from 172.67.74.226 (172.67.74.226): icmp_seq=3 ttl=53 time=63.5 ms
64 bytes from 172.67.74.226 (172.67.74.226): icmp_seq=4 ttl=53 time=33.3 ms
64 bytes from 172.67.74.226 (172.67.74.226): icmp_seq=5 ttl=53 time=148 ms
^C
--- ynov.com ping statistics ---
5 packets transmitted, 5 received, 0% packet loss, time 4009ms
rtt min/avg/max/mdev = 33.311/79.260/147.561/44.225 ms
```
```
[adam@Brazilia ~]$ sudo firewall-cmd --add-masquerade --permanent
[sudo] password for adam:
success
[adam@Brazilia ~]$ sudo firewall-cmd --reload
success
```
### 2. Accès internet clients
