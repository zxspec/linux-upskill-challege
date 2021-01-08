# Day 17 - From the source

https://github.com/snori74/linuxupskillchallenge/blob/master/17.md  
https://www.youtube.com/watch?v=a9_hry-8Hhw

## nmap sources

- Wget - The non-interactive network downloader.

download official source codes v7.80 from https://nmap.org/dist/nmap-7.80.tar.bz2

```shell
$ wget -v https://nmap.org/dist/nmap-7.80.tar.bz2
$ tar xvjf nmap-7.80.tar.bz2
```

## compiling and installing nmap from sources

```shell
$ sudo apt install build-essential
$ cd nmap-7.80
$ vi README.md
. . .
Ideally, you should be able to just type:

    ./configure
    make
    make install
```

### configure

#### missing `flex` package

```shell
$ ./configure
. . .
checking for flex... no
checking for lex... no
configure: error: Neither flex nor lex was found.
. . .

$ sudo apt install flex

```

#### missing `bison` package

```shell
$ ./configure
. . .
checking for bison... no
checking for byacc... no
checking for capable yacc/bison... insufficient
configure: error: yacc is insufficient to compile libpcap.
 libpcap requires Bison, a newer version of Berkeley YACC with support
 for reentrant parsers, or another YACC compatible with them.
configure: error: ./configure failed for libpcap

$ sudo apt install bison
```

#### final round

```shell
$ ./configure
config.status: creating config.h
            .       .
            \`-"'"-'/
             } 6 6 {
            ==. Y ,==
              /^^^\  .
             /     \  )  Ncat: A modern interpretation of classic Netcat
            (  )-(  )/
            -""---""---   /
           /   Ncat    \_/
          (     ____
           \_.=|____E
Configuration complete.

                    ___.-------.___
                _.-' ___.--;--.___ `-._
             .-' _.-'  /  .+.  \  `-._ `-.
           .' .-'      |-|-o-|-|      `-. `.
          (_ <O__      \  `+'  /      __O> _)
            `--._``-..__`._|_.'__..-''_.--'
                  ``--._________.--''
   ____  _____  ____    ____       _       _______
  |_   \|_   _||_   \  /   _|     / \     |_   __ \
    |   \ | |    |   \/   |      / _ \      | |__) |
    | |\ \| |    | |\  /| |     / ___ \     |  ___/
   _| |_\   |_  _| |_\/_| |_  _/ /   \ \_  _| |_
  |_____|\____||_____||_____||____| |____||_____|

  NMAP IS A POWERFUL TOOL -- USE CAREFULLY AND RESPONSIBLY
Configured with: ndiff zenmap nping zlib lua ncat
Configured without: localdirs openssl libssh2 nmap-update
Type make (or gmake on some *BSD machines) to compile.
WARNING: You are compiling without OpenSSL
WARNING: You are compiling without LibSSH2
```

### make and test run

```shell
$ make
. . .
gcc -o ncat -g -O2 -Wall  -L../libpcap  ncat_main.o ncat_connect.o ncat_core.o ncat_posix.o ncat_listen.o ncat_proxy.o ncat_ssl.o base64.o http.o util.o sys_wrap.o ncat_lua.o ../nsock/src/libnsock.a ../nbase/libnbase.a  -lpcap ./../liblua/liblua.a -lm -ldl
make[1]: Leaving directory '/home/user/nmap/nmap-7.80/ncat'
```

```shell
$ ./nmap localhost
. . .
Starting Nmap 7.80 ( https://nmap.org ) at 2021-01-08 22:55 CET
Nmap scan report for localhost (127.0.0.1)
Host is up (0.000060s latency).
Not shown: 999 closed ports

```

### installing

```shell
$ sudo make install
. . .
NMAP SUCCESSFULLY INSTALLED

$ where nmap
. . .
/usr/local/bin/nmap

```

### uninstalling

```shell
$ sudo make uninstall
. . .
NMAP SUCCESSFULLY INSTALLED

$ where nmap
. . .
nmap not found

```
