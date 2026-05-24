# Group ADM

## Checking Group Membership

```shell
secaudit@NIX02:~$ id
```

```output title="Output"
uid=1010(secaudit) gid=1010(secaudit) groups=1010(secaudit),4(adm)
```

## Abusing

```shell
secaudit@NIX02:~$ grep -r . /var/log
```
