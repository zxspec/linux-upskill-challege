# Day 2 - Basic navigation

https://github.com/snori74/linuxupskillchallenge/blob/master/02.md
https://www.youtube.com/watch?v=x_VBskTUzxg

## basic commands

- pwd - return working directory name (Print Working Directory);
- cd - Change Directory
- printenv - print all or part of environment
- ls - list directory contents
- mkdir - make directories
- touch - change file timestamps
- mv - move (rename) files
- cp - copy files and directories
- rmdir - remove **empty** directories
- rm - remove files or directories

```shell
$ pwd

$ cd /home
$ cd ~
$ cd $HOME

$ printenv

$ ls
$ ls -l
$ ls /var/log  -lstra --color=auto
$ mkdir /home/repos
$ touch test.md
$ mv test.md readme.md
$ cp readme.md readme.md.bak  # copy file
$ cp -r /home/ /tmp/home.tmp/ # copy directory
$ cp -r /home/ /tmp/home.tmp/ # copy directory
```

## command prompt configuration

[How to change the default shell prompt](https://access.redhat.com/solutions/505983)

PS1 is a primary prompt variable which holds \u@\h \W\\$ special bash characters.

- \u = username
- \h = hostname
- \W = current working directory
  <!-- end of the list -->

Default value `\u@\h \W\\$`  
This is the default structure of the bash prompt and is displayed every time a user logs in using a terminal.  
These default values are set in the `/etc/bashrc` file.

- export - Set export attribute for shell variables. http://linuxcommand.org/lc3_man_pages/exporth.html

```shell

$ export -p # display a list of all exported variables and functions
$ echo $PS1 # display current command prompt configuration
$  export PS1="\u at server \h: \w -> "
$  export PS1="\u at server \h: \W -> "
```

## looking for help

- man - an interface to the system reference manuals
- apropos - search the manual page names and descriptions
- tldr - short and practical version of man

```shell

$ man ls
$ apropos list
$ tldr ls
```

## extra

### directory stacks

[zsh directory stacks](http://zsh.sourceforge.net/Intro/intro_6.html)
shell commands that are present in ZSH and CSH

- dirs - shows directories stack
- pushd - puts the current directory on the stack, and changes to a new directory
- popd - pops a directory off the stack and changes to it

```shell

$ cd ~
$ cd /tmp
$ pushd /var/logs
$ popd # return back to /tmp
$ popd # return back to ~
```
