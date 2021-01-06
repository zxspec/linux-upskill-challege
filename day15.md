# 15 - Deeper into repositories...

https://github.com/snori74/linuxupskillchallenge/blob/master/15.md  
https://www.youtube.com/watch?v=DMenSNaMiD4

## repositories and packages

- apt-cache - query the APT cache
- `/etc/apt/sources.list` - list of curently used repositories

```
deb http://nl.archive.ubuntu.com/ubuntu/ focal main restricted

```

List of packages available to install

```shell
$ sudo apt-cache pkgnames
```

### package details

```shell
$ apt-cache show htop
```

Package dependencies

```shell
$ apt-cache depends htop
```

Who depends on `htop`

```shell
$ apt-cache rdepends htop
```

### add repository

- add-apt-repository - Adds a repository into the /etc/apt/sources.list or /etc/apt/sources.list.d or removes an existing one

#### add `universe` repo

```shell
$ sudo add-apt-repository universe
$ sudo apt update
```

#### add PPA repository

`ppa` is a Personal Package Archive  
[launchpad.net](https://launchpad.net) is a service hosting PPAs.

- [OpenShot: Experimental PPA - Mostly Stable](https://launchpad.net/~jonoomph/+archive/ubuntu/openshot-edge)
- [Neofetch](https://launchpad.net/~dawidd0811/+archive/ubuntu/neofetch)

add OpenShot PPA

```shell
$ sudo add-apt-repository ppa:jonoomph/openshot-edge
$ sudo apt update
```

add OpenShot PPA

```shell
$ sudo add-apt-repository ppa:dawidd0811/neofetch
$ sudo apt update
. . .
# one more line in repository list
Hit:4 http://ppa.launchpad.net/dawidd0811/neofetch/ubuntu focal InRelease
```

install package

```shell
$ sudo apt install neofetch
```

#### remove PPA or any repository

```shell
$ sudo add-apt-repository --remove ppa:jonoomph/openshot-edge
$ sudo apt update
```

add OpenShot PPA

```shell
$ sudo add-apt-repository --remove ppa:dawidd0811/neofetch
$ sudo apt update
```
