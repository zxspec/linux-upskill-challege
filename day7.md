# Day 7 - Installing Apache

https://github.com/snori74/linuxupskillchallenge/blob/master/07.md  
https://www.youtube.com/watch?v=VzXwO0qq-bg

## installing apache srv

```shell
$ sudo apt update
$ sudo apt upgrade
$ sudo systemctl status apache2
```

## check status

```shell
$ sudo systemctl status apache2
```

or from local machine

```shell
$ ssh -L 8080:127.0.0.1:80 ubuntu@ec2-35-159-18-151.eu-central-1.compute.amazonaws.com
$ nc 127.0.0.1 8080
```

## stop, start etc.

```shell
$ sudo systemctl stop apache2
$ sudo systemctl start apache2
$ sudo systemctl enable apache2
$ sudo systemctl disble apache2
```

## configuration

- configuration is located in `/etc/apache2/apache2.conf`
- default page is located in `/var/www/html/index.html`

## logs

- access log `/var/log/apache2/access.log`

## extra

https://www.digitalocean.com/community/tutorials/how-to-use-systemctl-to-manage-systemd-services-and-units

If you are unsure whether the service has the functionality to reload its configuration, you can issue the _reload-or-restart_ command.

```shell
$ sudo systemctl reload-or-restart <service>
$ systemctl is-active <service>
$ systemctl is-enabled <service>
$ systemctl is-failed <service>
```

### list

```shell
$ systemctl list-units
$ systemctl list-units --all --state=inactive
$ systemctl list-units --type=service
$ systemctl list-units --type=device
$ systemctl list-unit-files
```

### unit file

```shell
$ systemctl cat apache2.service
```

### dependencies

```shell
$ systemctl list-dependencies sshd.service
$ systemctl list-dependencies sshd.service --reverse
$ systemctl list-dependencies sshd.service --all
```

### service info

```shell
$ systemctl show sshd.service
$ systemctl show sshd.service -p Conflicts
```

### masking

`systemd` also has the ability to mark a unit as completely unstartable, automatically or manually, by linking it to `/dev/null`. This is called masking the unit

```shell
$ sudo systemctl mask apache2.service
$ systemctl list-unit-files | grep apache2 # to check that service is masked
$ sudo systemctl unmask apache2.service
```
