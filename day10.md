# Day 10 - Getting the computer to do your work for you

https://github.com/snori74/linuxupskillchallenge/blob/master/10.md  
https://www.youtube.com/watch?v=ktjabe8enxU

## cron

- cron -- daemon to execute scheduled commands (Vixie Cron)

```shell
$ vi /etc/crontab # edit existing jobs
```

add message every hour exactly at XX:30 min

```cron
30 *    * * *   root    echo $(date) "Shed message" >> /home/ubuntu/cron.messages
```

add message every Friday at 17:45

```cron
45 17    * * fri   root    echo "Fridat beer is soon" >> /home/ubuntu/friday.messages
```

add after each reboot

```cron
@reboot   root    echo "rebooted at $(date)" >> /home/ubuntu/reboot.messages
```

Also possible to use:

- @reboot
- @hourly
- @dialy
- @weekly
- @monthly
- @yearly

## extra

### systemctl list-timers

https://www.maketecheasier.com/use-systemd-timers-as-cron-replacement/

```shell
$ systemctl list-timers --all
$ sudo systemctl status man-db.timer
. . .
● man-db.timer - Daily man-db regeneration
     Loaded: loaded (/lib/systemd/system/man-db.timer; enabled; vendor preset: enabled)
     Active: active (waiting) since Wed 2020-12-30 20:37:09 CET; 12min ago
    Trigger: Thu 2020-12-31 00:00:00 CET; 3h 10min left
   Triggers: ● man-db.service
       Docs: man:mandb(8)

```

```shell
$ sudo systemctl start man-db.timer # start timer
```

### at

- at, batch, atq, atrm - queue, examine, or delete jobs for later execution

```shell
$ at -f test.sh -v 13:30
```

### anacron

- anacron - runs commands periodically
  more details: https://www.ibm.com/developerworks/linux/library/l-job-scheduling/index.html
