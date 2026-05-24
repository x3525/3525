# Plugins

## Find Plugins Directory

```shell
my@attack:~$ find / -wholename "*metasploit*plugins*" -type d 2> /dev/null
```

## Download Plugins

```shell
my@attack:~$ git clone https://github.com/darkoperator/Metasploit-Plugins.git
```

## Copy Plugin

```shell
my@attack:~$ sudo cp Metasploit-Plugins/pentest.rb /opt/metasploit/plugins
```

## Load Plugin

```shell
msf6 > load pentest
```
