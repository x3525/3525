# Cracking Wireless Handshakes

## MIC

### [Converting](https://hashcat.net/cap2hashcat/)

```shell
my@attack:~$ cap2hccapx CapFile HashFile
```

### Cracking the Handshakes

=== "NEW"

    ```shell
    my@attack:~$ hashcat -a 0 -m 22000 HashFile Wordlist
    ```

=== "OLD"

    ```shell
    my@attack:~$ hashcat -a 0 -m 2500 HashFile Wordlist --deprecated-check-disable
    ```

## PMKID

### Extracting

=== "NEW"

    ```shell
    my@attack:~$ hcxpcapngtool CapFile -o HashFile
    ```

=== "OLD"

    ```shell
    my@attack:~$ hcxpcaptool CapFile -z HashFile
    ```

### Cracking the Hash

=== "NEW"

    ```shell
    my@attack:~$ hashcat -a 0 -m 22000 HashFile Wordlist
    ```

=== "OLD"

    ```shell
    my@attack:~$ hashcat -a 0 -m 16800 HashFile Wordlist --deprecated-check-disable
    ```
