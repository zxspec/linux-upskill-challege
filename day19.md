# Day 19 - Inodes, symlinks and stat

https://github.com/snori74/linuxupskillchallenge/blob/master/19.md  
https://www.youtube.com/watch?v=3WrBVRaNCqQ

## links

### inodes

`inode` - Index Node

- df - report file system disk space usage
- stat - display file or file system status

```shell
$ df -i # list inode information instead of block usage
$ ls -i # show inodes in a file list
$ ls -i /home/user # show inode of a folde
$ ls -i /home/user/.ssh/known_hosts # show inode of a file
$ stat /home/user/.ssh/known_hosts
. . .
  File: /home/user/.ssh/known_hosts
  Size: 888       	Blocks: 8          IO Block: 4096   regular file
Device: 815h/2069d	Inode: 11420218    Links: 1
                            ^^^^^^

```

### symbolic or soft links

symlink is an inode referencing another inode.

- ln - make links between files
- stat - display file or file system status

```shell
$ ln -s /home/user1/.ssh/known_hosts ~/new_symlink_to_known_hosts
$ ls -l
. . .
lrwxrwxrwx  1 user1 user1   31 jan 10 18:11 new_symlink_to_known_hosts -> /home/user1/.ssh/known_hosts
^                                                                     ^^^^^^^^
|                                                                        |
link                                                                 reference
```

```shell
stat -L new_symlink_to_known_hosts ~/.ssh/known_hosts
  File: new_symlink_to_known_hosts
  Size: 888       	Blocks: 8          IO Block: 4096   regular file
Device: 815h/2069d	Inode: 11420218    Links: 1
                           ^^^^^^^^
                          same inode
. . .
  File: /home/user1/.ssh/known_hosts
  Size: 888       	Blocks: 8          IO Block: 4096   regular file
Device: 815h/2069d	Inode: 11420218    Links: 1
                           ^^^^^^^^
                          same inode
```

### hard links

Hard links are also referencing the same inode.

```shell
$ ln ~/.ssh/known_hosts new_hard_link
$ ls -lih ~/
11420218 -rw-r--r--  2 user1 user1  888 jan  2 22:09 new_hardlink_to_known_hosts
11551376 lrwxrwxrwx  1 user1 user1   31 jan 10 18:11 new_symlink_to_known_hosts -> /home/user1/.ssh/known_hosts
. . .
$ ls -lhi ~/.ssh/known_hosts
. . .
11420218 -rw-r--r-- 2 devdimon devdimon 888 jan  2 22:09 /home/user1/.ssh/known_hosts
                    ^
                    |
                    # of hard links
```

### comparison of hard and soft links

1. creating hard link would increase inode/file hard link counter
2. hard link works only with file but not directories
3. soft link has `l` type
4. soft might reference to non existing file/folder
5. hard link to the same file have the same inode
6. TBD

## aliases

```shell
$ alias # list of all aliases
. . .
-='cd -'
...=../..
....=../../..
.....=../../../..
......=../../../../..
1='cd -'
2='cd -2'
3='cd -3'

```

```shell
$ alias cls="clear" # add `cls` alias for `clear`

```

## extra

[Anatomy of the Linux file system](https://developer.ibm.com/tutorials/l-linux-filesystem/)
