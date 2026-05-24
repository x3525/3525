# RDP

## Port

| NUMBER | DESCRIPTION |
|---|---|
| 3389 | Microsoft Terminal Server (RDP) officially registered as Windows Based Terminal (WBT) |

## Nmap

```shell
my@attack:~$ sudo nmap 10.129.56.98 -p 3389 -Pn
```

## Service Interaction

### RDesktop

```shell
my@attack:~$ rdesktop 10.129.56.98:3389 -u 'htb-rdp' -p 'HTBRocks!' -d inlanefreight.htb -r disk:linux=/tmp
```

```shell
my@attack:~$ rdesktop 10.129.56.98:3389 -u 'htb-rdp' -p 'HTBRocks!' -a 8 -x m -z -D
```

### xFreeRDP

```shell
my@attack:~$ xfreerdp /v:10.129.56.98:3389 /u:'htb-rdp' /p:'HTBRocks!' /d:inlanefreight.htb /drive:linux,/tmp
```

```shell
my@attack:~$ xfreerdp /v:10.129.56.98:3389 /u:'htb-rdp' /p:'HTBRocks!' /proxy:socks5://127.0.0.1:9050
```

```shell
my@attack:~$ xfreerdp /v:10.129.56.98:3389 /u:'htb-rdp' /p:'HTBRocks!' /sec:rdp
```

```shell
my@attack:~$ xfreerdp /v:10.129.56.98:3389 /u:'htb-rdp' /p:'HTBRocks!' /tls-seclevel:0
```

```shell
my@attack:~$ xfreerdp /v:10.129.56.98:3389 /u:'htb-rdp' /p:'HTBRocks!' +enforce-tlsv1_2
```

```shell
my@attack:~$ xfreerdp /v:10.129.56.98:3389 /u:'htb-rdp' /p:'HTBRocks!' /dynamic-resolution /bpp:8 /network:modem /compression /gdi:hw /gfx:avc444 /rfx +clipboard -themes -wallpaper -fonts -glyph-cache
```

## Brute Forcing Credentials

### Hydra

```shell
my@attack:~$ hydra "rdp://10.129.56.98" -L usernames.txt -P passwords.txt
```

### [Crowbar](https://github.com/galkan/crowbar)

```shell
my@attack:~$ crowbar.py -b rdp -s 10.129.56.98/32 -U usernames.txt -C passwords.txt
```
