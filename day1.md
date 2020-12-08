# Day 1 - Accessing your server

https://www.reddit.com/r/linuxupskillchallenge/comments/k80ufq/day_1_accessing_your_server/

##

SSH extra

### Tunneling

https://linuxize.com/post/how-to-setup-ssh-tunneling/

#### Local Port Forwarding

1. Listen on server-side port 4444

```
$ nc -l 4444
```

2. initiate SSH connection with forwarding local port TCP 4000 to remote port TCP 4444

```
$ ssh -L 4000:ec2-18-185-26-6.eu-central-1.compute.amazonaws.com:4444 ubuntu@ec2-18-185-26-6.eu-central-1.compute.amazonaws.com
```

3. test connection with your browser http://localhost:4000
   or

```
$ nc localhost 4000
type anything and press enter
```

4. check that you see nc-output on the server-side console

### TBD

1. [passwordless login](https://linuxize.com/post/how-to-setup-passwordless-ssh-login/)
2. [ssh config](https://linuxize.com/post/using-the-ssh-config-file/)
