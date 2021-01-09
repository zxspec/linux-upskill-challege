# Day 18 - Log rotation

https://github.com/snori74/linuxupskillchallenge/blob/master/18.md  
https://www.youtube.com/watch?v=sd5NFUo5JYM

## logrotate deamon

- logrotate ‐ rotates, compresses, and mails system logs
- global level configuration is in `/etc/logrotate.conf`
- app level configuration is in `/etc/logrotate.d`. When individual packages are installed on the system, they drop the log rotation configuration information in this directory.

```shell
$ vi /etc/logrotate.d/apt
. . .
/var/log/apt/term.log {
  rotate 12
  monthly
  compress
  missingok
  notifempty
}

/var/log/apt/history.log {
  rotate 12
  monthly
  compress
  missingok
  notifempty
}
```

```shell
$ ls /var/log/apt/
. . .
-rw-r--r-- 1 root root  74000 jan  9 00:57 eipp.log.xz
-rw-r--r-- 1 root root  46684 jan  9 00:57 history.log
-rw-r--r-- 1 root root  33421 dec 28 22:10 history.log.1.gz
-rw-r----- 1 root adm  197703 jan  9 00:57 term.log
-rw-r----- 1 root adm   27745 dec 28 22:10 term.log.1.gz

```

## journalctl

- journalctl - Query the systemd journal

```shell
$  journalctl -b # all message since boot
$  journalctl --since today
$ journalctl --priority=1 # only critical messages
$ journalctl --priority=3 # only error messages
$ journalctl -f # show latest logs first

```

## extra

[HowTo: The Ultimate Logrotate Command Tutorial with 10 Examples](https://www.thegeekstuff.com/2010/07/logrotate-examples/)

```shell
$ where logrotate
. . .
/usr/sbin/logrotate
/sbin/logrotate
```

`/etc/cron.daily/logrotate` is used to execute logrotate every day

### configuration options

- size - limit max size of the current log file: `size 1k`
- create - create with specified permission for user and group: `create 700 user group`
- rotate - limits the number of log file rotation: `rotate 4`
- copytruncate - continue to write the log information in the newly created file after rotating the old log file. TBD
- compress
- dateext - rotate the old log file with date in the log filename: `output.log => output.log-20100609.gz`  
   This would work only once in a day.
- monthly, daily, weekly
- postrotate - run script after log rotation: `postrotate /home/user/myscript.sh`
- maxage - remove logs older N days: `maxage 42`
- missingok
- compresscmd - type of compression command should be used: `/bin/bzip2`
- compressext - compress extension: `.bz2`
