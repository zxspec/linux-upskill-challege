# Day 11 - Finding things...

https://github.com/snori74/linuxupskillchallenge/blob/master/11.md  
https://www.youtube.com/watch?v=gQ9nP9PN8KA

## find things

- which - locate a command
- find - search for files in a directory hierarchy
- locate - list files in databases that match a pattern

```shell
$ which vim
. . .
/usr/bin/vim
```

```shell
$ sudo find /var/ -name access.log
$ find /home/ -mtime -2 # find files modified in last 2*24 hours
$ find /home/ -atime -7 # find files accessed in last 7*24 hours
```

```shell
$ sudo updatedb
$ locate access.log
$ grep -R -i "error" /var/log/sys* # find in files
```

## extra

[25 Useful find Command Practical Examples in Linux](https://www.linuxtechi.com/25-find-command-examples-for-linux-beginners/)
find parameters:

- name - file name, supports globbing
- iname - same as name but case insensitive
- type - use "d" for directories, "f" for files
- not - use it in combination with other flags
- regex
- o - OR
- perm - permissions
- user
- group
- empty
- exec

```shell
$ sudo find /var/log -type d # find directories only
$ sudo find /var/log/apt -type f # find files only
$ sudo find /var/log -name a*.log # find all .log files starting with "a" in /var/log directory
$ sudo find /var /run -iname *.log # find .log files in /var and /run directories
$ sudo find /var/log -not -iname *.log # find all non-log files in /var/log directory
$ sudo find /etc  -iname *.mount -o -name *.conf # find .mount OR .conf files
$ sudo find /var -perm 400 # find all files with permission 400
$ find ~ -perm /a=x # find all executable files in home directory
$ find ~ -perm /u=r # find all read-only files in home directory
$ users
$ sudo find /dev -user ubuntu # find files owned by user "ubuntu" in /dev directory
$ groups
$  sudo find / -group sudo # find all files owned by group "sudo"
$ sudo find / -size +50M -size -100M # find all files >50MB and less than 100MB
$ find ~ -empty -type f # find empty files in home directory
$ find ~ -empty -type d # find empty directories in home directory
```

### find -exec

Find largest and smallest files

```shell
$ find . -type f -exec ls -s {} \;
$ find . -type f -exec ls -s {} \; | sort -n -r | head -3
$ find . -type f -exec ls -s {} \; | sort -n | head -3
```

Print all files in home directory with 644 permission

```shell
$ find ~ -type f -perm 644 -print
```

Cahnge files permission to 777 of all files in home directory with 644 permission

```shell
$ find ~ -type f -perm 644 -print -exec chmod 777 {} \;
```

Find all non-log files in /var/log/apache2 directory and delete those

```shell
$ find /var/log/apache2/ -not -name *.log -type f -print -exec rm -f  {} \;
```
