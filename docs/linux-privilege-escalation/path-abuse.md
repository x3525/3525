# PATH Abuse

## Creating the Script

```shell
htb-student@NIX02:~$ echo 'echo "PATH ABUSE"' > ls
htb-student@NIX02:~$ chmod +x ls
```

## Updating the PATH

```shell
htb-student@NIX02:~$ PATH=$HOME:$PATH
htb-student@NIX02:~$ export PATH
```

## Abusing

```shell
htb-student@NIX02:~$ ls
```

```output title="Output"
PATH ABUSE
```
