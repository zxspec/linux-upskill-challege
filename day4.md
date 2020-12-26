# Day 4 - Installing software, exploring the file structure

https://github.com/snori74/linuxupskillchallenge/blob/master/04.md  
https://www.youtube.com/watch?v=d8JzxgGNAx4  

## adding software with _apt_

```shell
$ apt search "midnight commander"
$ sudo apt install mc
```

## fs hierarchy
- hier - description of the filesystem hierarchy

## extra


###  Repositories - CommandLine
https://help.ubuntu.com/community/Repositories/CommandLine

repositories mirrors `/etc/apt/sources.list`, `/etc/apt/sources.list.d/`, 
add repository:
```shell
$ sudo add-apt-repository "deb http://us.archive.ubuntu.com/ubuntu/ saucy universe multiverse"
$ sudo apt-get update
```