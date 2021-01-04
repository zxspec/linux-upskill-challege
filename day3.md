# Day 3 - Power trip!

https://github.com/snori74/linuxupskillchallenge/blob/master/03.md  
https://www.youtube.com/watch?v=B6fDvmmh2_Q  

## sudo

- sudo, sudoedit — execute a command as another user

```shell
$ reboot # Permission denied
$ less /etc/shadow # -> Permission denied
$ ls -l /etc/shadow # -> -rw-r----- 1 root shadow 962 Dec 24 10:51 /etc/shadow
$ sudo less /etc/shadow
$ sudo reboot # Permission denied
```

## logs

- grep, egrep, fgrep, rgrep - print lines that match patterns

```shell
$ less /var/log/auth.log
$ grep "sudo" /var/log/auth.log
```

## system settings

### static hostname

- hostnamectl - Control the system hostname
- hostname - show or set the system's host name
- domainname - show or set the system's NIS/YP domain name
- ypdomainname - show or set the system's NIS/YP domain name
- nisdomainname - show or set the system's NIS/YP domain name
- dnsdomainname - show the system's DNS domain name

```shell
$ hostname
$ hostnamectl
$  sudo hostnamectl set-hostname "zxspec"
```

### timezone

- timedatectl - Control the system time and date

```shell
$ timedatectl
$ tldr timedatectl
$ timedatectl list-timezones
$ timedatectl list-timezones
$ sudo timedatectl set-timezone Europe/Amsterdam
```

## extra

[Hardening SSH](https://medium.com/@jasonrigden/hardening-ssh-1bcb99cd4cef)
