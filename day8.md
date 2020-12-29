# Day 8 - the infamous "grep"...

https://github.com/snori74/linuxupskillchallenge/blob/master/08.md  
https://www.youtube.com/watch?v=kG5JGJN5iTc

## operations with text

- echo - display a line of text
- cat - concatenate files and print on the standard output
- tac - concatenate and print files in reverse
- head - output the first part of files
- tail - output the last part of files
- wc - print newline, word, and byte counts for each file
- uniq - report or omit repeated lines
- cut - remove sections from each line of files
- grep, egrep, fgrep, rgrep - print lines that match patterns

```shell
$ echo "hello world"
$ echo $PWD
$ cat .bashrc
$ cat -n .bashrc
$ cat file1 file2
$ tac .bashrc
$ head -5 .bashrc
$ tail -5 .bashrc
$ wc -l .profile # print lines count
$ sort /var/log/apache2/access.log
$ uniq /var/log/apache2/access.log
$ cut -d":" -f1 /etc/passwd
$ grep "127.0.0.1" /var/log/apache2/access.log
```

## stream redirect

redirect program output to a new file or owerwrite existing

```
$ ls -lsa > list.txt
```

redirect program output to a new file or append to existing

```
$ ls -lsa /etc >> list.txt
```

redirect program output to a next program

```
$ grep "root" /var/log/auth.log | grep "[0-9]\{1,3\}\.[0-9]\{1,3\}\.[0-9]\{1,3\}\.[0-9]\{1,3\}"
$ grep "root" /var/log/auth.log | grep -o "[0-9]\{1,3\}\.[0-9]\{1,3\}\.[0-9]\{1,3\}\.[0-9]\{1,3\}" | sort | uniq
```

## extra

### sed

[SED Tutorial Basic Substitution Linux Shell BASH](https://www.youtube.com/watch?v=32waL1Z9XK0)

Make "root" more visible in an output

```shell
$ cat /var/log/auth.log | sed "s/root/>>>ROOT<<</g"
. . .
Dec 29 22:17:01 zxspec CRON[22363]: pam_unix(cron:session): session closed for user >>>ROOT<<<
```

Replace in a file and save changes `-i`

```shell
$ sed -i  "s/root/>>>ROOT<<</g" /var/log/auth.log
```

### awk

https://www.youtube.com/watch?v=fRZvwBevctA
