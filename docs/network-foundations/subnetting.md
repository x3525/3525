# Subnetting

## Example

| IPV4 ADDRESS | SUBNET MASK | CIDR |
|---|---|---|
| 192.168.12.160 | 255.255.255.192 | 192.168.12.160/26 |

## Network Part

| 1ST OCTET | 2ND OCTET | 3RD OCTET | 4TH OCTET | DECIMAL |
|---|---|---|---|---|
| {==11000000==} | {==10101000==} | {==00001100==} | {==10==}100000 | 192.168.12.160/{==26==} |
| {==11111111==} | {==11111111==} | {==11111111==} | {==11==}000000 | {==255.255.255.192==} |

## Host Part

| 1ST OCTET | 2ND OCTET | 3RD OCTET | 4TH OCTET | DECIMAL |
|---|---|---|---|---|
| 11000000 | 10101000 | 00001100 | 10{==100000==} | 192.168.12.160/26 |
| 11111111 | 11111111 | 11111111 | 11{==000000==} | 255.255.255.192 |

## Separation

!!! abstract

    Network ve host ayrımı belirlenir.

| 1ST OCTET | 2ND OCTET | 3RD OCTET | 4TH OCTET | DECIMAL |
|---|---|---|---|---|
| 11000000 | 10101000 | 00001100 | 10 100000 | 192.168.12.160/26 |
| {==11111111==} | {==11111111==} | {==11111111==} | {==11==} 000000 | 255.255.255.192 |

## Network Address

!!! abstract

    Host bitleri 0 yapılır.

| 1ST OCTET | 2ND OCTET | 3RD OCTET | 4TH OCTET | DECIMAL |
|---|---|---|---|---|
| 11000000 | 10101000 | 00001100 | 10 {==000000==} | {==192.168.12.128==}/26 |
| {==11111111==} | {==11111111==} | {==11111111==} | {==11==} 000000 | 255.255.255.192 |

## Broadcast Address

!!! abstract

    Host bitleri 1 yapılır.

| 1ST OCTET | 2ND OCTET | 3RD OCTET | 4TH OCTET | DECIMAL |
|---|---|---|---|---|
| 11000000 | 10101000 | 00001100 | 10 {==111111==} | {==192.168.12.191==}/26 |
| {==11111111==} | {==11111111==} | {==11111111==} | {==11==} 000000 | 255.255.255.192 |

## Subnetting Into Smaller Networks

Mevcut ağı 4 adet alt ağa bölelim:

* 2^H = 4
* Alt ağ maskesinin host kısmına eklenecek 1 adedi H adet olmalıdır.

| 1ST OCTET | 2ND OCTET | 3RD OCTET | 4TH OCTET | DECIMAL |
|---|---|---|---|---|
| 11000000 | 10101000 | 00001100 | 1000 0000 | 192.168.12.128/{==28==} |
| {==11111111==} | {==11111111==} | {==11111111==} | 11{==11==} 0000 | {==255.255.255.240==} |

* Alt ağ maskesinin host kısmına H adet 1 ekledikten sonra geriye 4 adet 0 kalır.
* 2^4 = A
* Her bir alt ağ için A adet IP adresi mevcuttur.

| SUBNET NUMBER | NETWORK ADDRESS | FIRST HOST | LAST ADDRESS | BROADCAST ADDRESS |
|---|---|---|---|---|
| 1 | {==192.168.12.128==} | 192.168.12.129 | 192.168.12.142 | {==192.168.12.143==} |
| 2 | {==192.168.12.144==} | 192.168.12.145 | 192.168.12.158 | {==192.168.12.159==} |
| 3 | {==192.168.12.160==} | 192.168.12.161 | 192.168.12.174 | {==192.168.12.175==} |
| 4 | {==192.168.12.176==} | 192.168.12.177 | 192.168.12.190 | {==192.168.12.191==} |

## Record Route Field

```shell
my@attack:~$ ping 10.129.143.158 -c 1 -R
```

```output title="Output"
PING 10.129.143.158 (10.129.143.158) 56(124) bytes of data.
64 bytes from 10.129.143.158: icmp_seq=1 ttl=63 time=11.7 ms
RR:     10.10.14.38
        10.129.0.1
        10.129.143.158
        10.129.143.158
        10.10.14.1
        10.10.14.38

--- 10.129.143.158 ping statistics ---
1 packets transmitted, 1 received, 0% packet loss, time 0ms
rtt min/avg/max/mdev = 11.688/11.688/11.688/0.000 ms
```
