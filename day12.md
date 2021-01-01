# Day 12 - Copying with SFTP

https://github.com/snori74/linuxupskillchallenge/blob/master/12.md  
https://www.youtube.com/watch?v=qjd5eazfoC0

## sftp

- sftp — OpenSSH secure file transfer

```shell
$ sftp ubuntu@ec2-35-159-18-151.eu-central-1.compute.amazonaws.com
$ sftp -i ~/.ssh/aws-linux-upskill-challenge.pem ubuntu@ec2-35-159-18-151.eu-central-1.compute.amazonaws.com
. . .
> pwd
. . .
Remote working directory: /home/ubuntu
> lpwd
. . .
Local working directory: /Users/user1
>exit
```

- `help` - list of supported commands
- `ls` - remote files list
- `lls` - local files list
- `put` - upload local file to remote location
- `get` - download file from remote location
- `mput` - upload multiple local files to remote location
- `mget` - download multiple files from remote location
- `rm` - delete remote file

```sftp
> lls
> put test_file
> ls
> get cron.messages
> lls
> mput -R local_folder optional_remote_folder
> ls optional_remote_folder
> mget -R remote_folder optional_local_folder
> lls optional_local_folder
> rm optional_remote_folder/test01.txt
```

## rsync

- rsync - a fast, versatile, remote (and local) file-copying tool

```shell
rsync -e "ssh -i ~/.ssh/aws-linux-upskill-challenge.pem" -av ~/local_dir/ ubuntu@ec2-35-159-18-151.eu-central-1.compute.amazonaws.com:remote_dir
```

some keys:

- -n, --dry-run - just to check what is going to be synchronized
- -r, --recursive - This tells rsync to copy directories recursively.
- -P, --progress
