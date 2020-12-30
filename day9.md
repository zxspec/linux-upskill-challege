# Day 9 - Ports, open and closed

https://github.com/snori74/linuxupskillchallenge/blob/master/09.md  
https://www.youtube.com/watch?v=47BWW-SyAa8

## basic network utils

- netstat - Print network connections, routing tables, interface statistics, masquerade connections, and multicast memberships
- ss - another utility to investigate sockets
- nmap - Network exploration tool and security / port scanner

```shell
$ netstat
$ netstat -l # listening ports
$ ss -ltp # listening TCP ports
$ ss -lup # listening UDP ports
```

### nmap

```shell
$ nmap localhost
```

## firewall

### ufw

- ufw - program for managing a netfilter firewall

```shell
$ sudo ufw status
$ sudo ufw deny http
$ sudo ufw enable # if status was inactive
$ sudo ufw disable
```

### iptables

- iptables/ip6tables — administration tool for IPv4/IPv6 packet filtering and NAT

```shell
$ sudo iptables -L
```

## extra

https://www.thegeekstuff.com/2012/08/iptables-log-packets/  
http://www.pettingers.org/code/firewall.html
