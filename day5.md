# Day 5 - More or less...

https://github.com/snori74/linuxupskillchallenge/blob/master/05.md  
 https://www.youtube.com/watch?v=d8JzxgGNAx4  

## text pagination
- more - file perusal filter for crt viewing
- less - opposite of more
```shell
$ more /var/log/auth.log
$ less /var/log/auth.log
```
### less shortcuts
q => quit
h => help  
/ => search  
n => next search result  
N => previous search result  

## history
```shell
$ history
$ history -10 # last 10 commands
$ !10 # add 10th command from history to command line
$ !! # add last command from history to command line
$ !sudo # add last sudo command from history to command line
$ less ~/.bash_history # bash history
$ less ~/.zsh_history # zsh history
```

## dot-files
```shell
ls -al ~/
less ~/.zshrc
less ~/.zsh_history
less ~/.bashrc
less ~/.bash_history
```