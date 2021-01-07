# Day 16 - 'tar' and friends...

https://github.com/snori74/linuxupskillchallenge/blob/master/16.md  
https://www.youtube.com/watch?v=r2Rfg6x-5MQ

## compressing

Compression is about reducing size

- tar - an archiving utility; originated from Tape ARchiving.
- du - estimate file space usage

```shell
$ du -h big-file
. . .
2.7M big-file

$ gzip big-file
$ du -h big-file.gz
. . .
380K
```

### decompressing

```shell
$ gunzip big-file.gz
```

## archiving

Archiving is about creating single archive from multiple files;

- tar - an archiving utility  
  c = create  
  f = file  
  t = table of archive content  
  v = verbosely show progress  
  z = zip (compress)  
  j = bz2 (compress)  
  x = extract  
  W = verify

Combine those files into a single without compression

```shell
$ tar cf archive.tar file1 file2 file3 big-file
```

View archive content without unpacking it

```shell
$ tar cf archive.tar file1 file2 file3 big-file
```

Combine those files into a single with compression

```shell
$ tar czf archive.tar.gz file1 file2 file3 big-file
                     ^^^^
                    archived
```

Extract archive in current folder

```shell
$ tar xfv archive.tar.gz
```

Extract archive in already existing folder

```shell
$ tar xfv archive.tar.gz -C existing_folder
```

## extra

[18 Tar Command Examples in Linux](https://www.tecmint.com/18-tar-command-examples-in-linux/)

```shell
$ tar cvfz arc.tar.gz file1 file2 file0* # create zip-archive
$ tar cvfj arc.tar.bz2 file1 file2 file0* # create bz2-archive
$ tar xvf arc.tar.gz file1 file2 # extract 2 files from archive
$ tar cvfW arc.tar file0*# create archive and verify it, does not work with compressed archives
```
