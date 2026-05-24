# Hashcat Attack Types

## [Dictionary Attack](https://hashcat.net/wiki/doku.php?id=dictionary_attack)

```shell
my@attack:~$ hashcat -a 0 -m HashType Hash Wordlist
```

```shell
my@attack:~$ hashcat -a 0 -m 0 187ef4436122d1cc2f40dc2b92f0eba0 ab.txt
```

## [Combinator Attack](https://hashcat.net/wiki/doku.php?id=combinator_attack)

```shell
my@attack:~$ hashcat -a 1 -m HashType Hash Wordlist Wordlist
```

```shell
my@attack:~$ hashcat -a 1 -m 0 187ef4436122d1cc2f40dc2b92f0eba0 a.txt b.txt
```

## [Mask Attack](https://hashcat.net/wiki/doku.php?id=mask_attack)

```shell
my@attack:~$ hashcat -a 3 -m HashType Hash Mask -1 CustomCharset -2 CustomCharset -3 CustomCharset -4 CustomCharset
```

```shell
my@attack:~$ hashcat -a 3 -m 0 187ef4436122d1cc2f40dc2b92f0eba0 '?1?1' -1 '?l'
```

| PLACEHOLDER | MEANING |
|---|---|
| ?l | Lower case characters |
| ?u | Upper case characters |
| ?d | Numbers |
| ?h | 0123456789abcdef |
| ?H | 0123456789ABCDEF |
| ?s | Symbols |
| ?a | ?l?u?d?s |
| ?b | 0x00 - 0xff |

## [Hybrid Attack](https://hashcat.net/wiki/doku.php?id=hybrid_attack)

### Append

```shell
my@attack:~$ hashcat -a 6 -m HashType Hash Wordlist Mask
```

```shell
my@attack:~$ hashcat -a 6 -m 0 187ef4436122d1cc2f40dc2b92f0eba0 a.txt '?l'
```

### Prepend

```shell
my@attack:~$ hashcat -a 7 -m HashType Hash Mask Wordlist
```

```shell
my@attack:~$ hashcat -a 7 -m 0 187ef4436122d1cc2f40dc2b92f0eba0 '?l' b.txt
```
