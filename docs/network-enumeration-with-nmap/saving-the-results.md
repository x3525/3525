# Saving the Results

## All Formats

```shell
my@attack:~$ sudo nmap 10.129.2.47 -p- -oA results
```

## Normal Output

```shell
my@attack:~$ sudo nmap 10.129.2.47 -p- -oN results.nmap
```

## XML Output

```shell
my@attack:~$ sudo nmap 10.129.2.47 -p- -oX results.xml
```

## Grepable Output

```shell
my@attack:~$ sudo nmap 10.129.2.47 -p- -oG results.gnmap
```

## Style Sheets

```shell
my@attack:~$ xsltproc results.xml -o results.html
```
