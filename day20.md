# Day 20 - Scripting

https://github.com/snori74/linuxupskillchallenge/blob/master/20.md  
https://www.youtube.com/watch?v=G7GyMuyauVk  
https://livialima.net/blog/2020-12-20-linuxupskill-day20.html

## scripting

_test.sh_

```shell
#!/bin/bash
# only comments on this line
echo "line with comments" # more comments
echo "You are $USER and your current folder is $PWD"
# declare variable on the line above
LOG="/var/log/auth.log"
echo "reading $LOG...
PATTERN="session opened for user root"
greep -i "$PATTERN" $LOG
# parameters
if [ -z $1 ]
then
    echo "Not enough parameters"
    exit 0
fi
echo "param 0: $0"
echo "param 1: $1"
echo "param 2: $2"
```

make script executable:

```shell
$ chmod +x ./test.sh
$ ./test.sh
```

## extra

[Bash scripting Tutorial](https://linuxconfig.org/bash-scripting-tutorial)
