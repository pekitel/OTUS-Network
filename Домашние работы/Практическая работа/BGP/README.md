# Задание

### Настроите eBGP между офисом Москва и двумя провайдерами - Киторн и Ламас.
### Настроите eBGP между провайдерами Киторн и Ламас.
### Настроите eBGP между Ламас и Триада.
### Настроите eBGP между офисом С.-Петербург и провайдером Триада.
### Организуете IP доступность между пограничным роутерами офисами Москва и С.-Петербург.

## Карта сети

![eBGP](https://user-images.githubusercontent.com/112701413/206729861-52e52891-6fe1-41f1-ae40-3c513aca7772.jpg)



## ***Решил добавить линк между R14 и R15 для дальнейшей настройки BGP*** 
| Hosts      | Ports    | Network IPv4    | Network IPv6                   | link-local |    Description    | 
|:----------:|:--------:|:---------------:|:------------------------------:|:----------:|:-----------------:|
| R14        | e1/0     | 77.37.144.253/30| 2001:ABCD:EEBB:AAAA:7::1/80    | FE80::14   | to --> R15        |
| R15        | e1/0     | 77.37.144.254/30| 2001:ABCD:EEBB:AAAA:7::2/80    | FE80::15   | to --> R14        |

## ***И добавил ipv6 адреса на loopback интерфайсах для роутеров провайдера ТРИАДА***
| Hosts      | Network IPv6                |
|:----------:|:---------------------------:|
| R23        | 2002:ABCD:EEBB:CCCC::23/128 |
| R24        | 2002:ABCD:EEBB:CCCC::24/128 |
| R25        | 2002:ABCD:EEBB:CCCC::25/128 |
| R26        | 2002:ABCD:EEBB:CCCC::26/128 |
### ***Настроите eBGP между офисом Москва и двумя провайдерами - Киторн и Ламас*** 
### ***Настроите eBGP между провайдерами Киторн и Ламас*** 

**R14**

```
R14>en
R14#conf t
R14(config)#router bgp 1001
R14(config-router)#bgp router-id 14.14.14.14
R14(config-router)#neighbor 82.138.2.1 remote-as 101
R14(config-router)#neighbor 2000:ABCD:EEBB:FFFF:1::1 remote-as 101
R14(config-router)#address-family ipv4 unicast
R14(config-router-af)#neighbor 82.138.2.1 activate
R14(config-router-af)#network 82.138.2.0 mask 255.255.255.252
R14(config-router-af)#exit-address-family
R14(config-router)#address-family ipv6 unicast
R14(config-router-af)#neighbor 2000:ABCD:EEBB:FFFF:1::1 activate
R14(config-router-af)#network 2000:ABCD:EEBB:FFFF:1::0/80
R14(config-router-af)#end
R14#wr
```
```
R14#show ip bgp summary

Neighbor        V           AS MsgRcvd MsgSent   TblVer  InQ OutQ Up/Down  State/PfxRcd
82.138.2.1      4          101     128     122       33    0    0 01:34:52        0
```
```
R14#show ip bgp ipv6 unicast summary

Neighbor        V           AS MsgRcvd MsgSent   TblVer  InQ OutQ Up/Down  State/PfxRcd
2000:ABCD:EEBB:FFFF:1::1
                4          101     955     952       24    0    0 14:15:26        0
```

**R15**

```
R15>en
R15#conf t
R15(config)#router bgp 1001
R15(config-router)#bgp router-id 15.15.15.15
R15(config-router)#neighbor 77.94.165.1 remote-as 301
R15(config-router)#neighbor 1999:ABCD:EEBB:FFFF:1::1 remote-as 301
R15(config-router)#address-family ipv4 unicast
R15(config-router-af)#neighbor 77.94.165.1 activate
R15(config-router-af)#network 77.94.165.0 mask 255.255.255.252
R15(config-router-af)#exit-address-family
R15(config-router)#address-family ipv6 unicast
R15(config-router-af)#neighbor 1999:ABCD:EEBB:FFFF:1::1 activate
R15(config-router-af)#network 1999:ABCD:EEBB:FFFF:1::0/80
R15(config-router-af)#end
R15#wr
```
```
R15#show ip bgp summary

Neighbor        V           AS MsgRcvd MsgSent   TblVer  InQ OutQ Up/Down  State/PfxRcd
77.94.165.1     4          301     158     148    19851    0    0 01:49:12        0
```
```
R15#show ip bgp ipv6 unicast summary

Neighbor        V           AS MsgRcvd MsgSent   TblVer  InQ OutQ Up/Down  State/PfxRcd
1999:ABCD:EEBB:FFFF:1::1
                4          301     975     971       26    0    0 14:33:57        0
```
**R21**

```
R21>en
R21#conf t
R21(config)#router bgp 301
R21(config-router)#bgp router-id 21.21.21.21
R21(config-router)#neighbor 77.94.165.2 remote-as 1001
R21(config-router)#neighbor 82.138.2.5 remote-as 101
R21(config-router)#neighbor 109.72.1.21 remote-as 520
R21(config-router)#neighbor 1999:ABCD:EEBB:FFFF:1::2 remote-as 1001
R21(config-router)#neighbor 2000:ABCD:EEBB:FFFF:2::1 remote-as 101
R21(config-router)#neighbor 2002:ABCD:EEBB:FFFF:9::1 remote-as 520
R21(config-router)#address-family ipv4 unicast
R21(config-router-af)#neighbor 77.94.165.2 activate
R21(config-router-af)#neighbor 82.138.2.5 activate
R21(config-router-af)#neighbor 109.72.1.21 activate
R21(config-router-af)#exit-address-family
R21(config-router)#address-family ipv6 unicast
R21(config-router-af)#neighbor 1999:ABCD:EEBB:FFFF:1::2 activate
R21(config-router-af)#neighbor 2000:ABCD:EEBB:FFFF:2::1 activate
R21(config-router-af)#neighbor 2002:ABCD:EEBB:FFFF:9::1 activate
```
```
R21#show ip bgp summary

Neighbor        V           AS MsgRcvd MsgSent   TblVer  InQ OutQ Up/Down  State/PfxRcd
77.94.165.2     4         1001      49      63       27    0    0 00:35:54        2
82.138.2.5      4          101      40      35       27    0    0 00:09:24        5
109.72.1.21     4          520      59      56       27    0    0 00:35:53        4
```
```
R21#show ip bgp ipv6 unicast summary

Neighbor        V           AS MsgRcvd MsgSent   TblVer  InQ OutQ Up/Down  State/PfxRcd
1999:ABCD:EEBB:FFFF:1::2
                4         1001    1060    1066       21    0    0 15:47:07        2
2000:ABCD:EEBB:FFFF:2::1
                4          101    1055    1053       21    0    0 15:47:10        2
2002:ABCD:EEBB:FFFF:9::1
                4          520     909     913       21    0    0 13:38:23        4
```
**R22**

```
R22>en
R22#conf t
R22(config)#router bgp 101
R22(config-router)#bgp router-id 22.22.22.22
R22(config-router)#neighbor 82.138.2.2 remote-as 1001
R22(config-router)#neighbor 82.138.2.6 remote-as 301
R22(config-router)#neighbor 109.72.1.17 remote-as 520
R22(config-router)#neighbor 2000:ABCD:EEBB:FFFF:1::2 remote-as 1001
R22(config-router)#neighbor 2000:ABCD:EEBB:FFFF:2::2 remote-as 301
R22(config-router)#neighbor 2002:ABCD:EEBB:FFFF:8::1 remote-as 520
R22(config-router)#address-family ipv4 unicast
R22(config-router-af)#neighbor 82.138.2.2 activate
R22(config-router-af)#neighbor 82.138.2.6 activate
R22(config-router-af)#neighbor 109.72.1.17 activate
R22(config-router-af)#exit-address-family
R22(config-router)#address-family ipv6 unicast
R22(config-router-af)#neighbor 2000:ABCD:EEBB:FFFF:1::2 activate
R22(config-router-af)#neighbor 2000:ABCD:EEBB:FFFF:2::2 activate
R22(config-router-af)#neighbor 2002:ABCD:EEBB:FFFF:8::1 activate
R22(config-router-af)#end
R22#wr
```
```
R22#sh ip bgp summary

Neighbor        V           AS MsgRcvd MsgSent   TblVer  InQ OutQ Up/Down  State/PfxRcd
82.138.2.2      4         1001      51      59      226    0    0 00:33:21        2
82.138.2.6      4          301      34      39      226    0    0 00:08:50        5
109.72.1.17     4          520      24      32      226    0    0 00:08:35        4
```
```
R22#show ip bgp ipv6 unicast summary

Neighbor        V           AS MsgRcvd MsgSent   TblVer  InQ OutQ Up/Down  State/PfxRcd
2000:ABCD:EEBB:FFFF:1::2
                4         1001    1133    1136       32    0    0 16:51:02        6
2000:ABCD:EEBB:FFFF:2::2
                4          301    1120    1125       32    0    0 16:48:24        6
2002:ABCD:EEBB:FFFF:8::1
                4          520       7      13       32    0    0 00:01:59        4

```
### ***Настроите eBGP между Ламас и Триада *** 


**R24**

```
R24>en
R24#conf t
R24(config)#router bgp 520
R24(config-router)#bgp router-id 24.24.24.24
R24(config-router)#neighbor 109.72.1.22 remote-as 301
R24(config-router)#neighbor 109.72.1.38 remote-as 2042
R24(config-router)#neighbor 2002:ABCD:EEBB:FFFF:9::2 remote-as 301
R24(config-router)#neighbor 2002:ABCD:EEBB:FFFF:A::2 remote-as 301
R24(config-router)#address-family ipv4 unicast
R24(config-router-af)#neighbor 109.72.1.22 activate
R24(config-router-af)#neighbor 109.72.1.38 activate
R24(config-router-af)#exit-address-family
R24(config-router)#address-family ipv6 unicast
R24(config-router-af)#neighbor 2002:ABCD:EEBB:FFFF:9::2 activate
R24(config-router-af)#neighbor 2002:ABCD:EEBB:FFFF:A::2 activate
```
```
R24#show ip bgp summary

Neighbor        V           AS MsgRcvd MsgSent   TblVer  InQ OutQ Up/Down  State/PfxRcd
109.72.1.21     4          520      59      56       27    0    0 00:35:53        4
109.72.1.38     4         2042     196     194       64    0    0 02:33:32        1
```
```
R24#show ip bgp ipv6 unicast summary

Neighbor        V           AS MsgRcvd MsgSent   TblVer  InQ OutQ Up/Down  State/PfxRcd
2002:ABCD:EEBB:FFFF:9::2
                4          301    1025    1021       15    0    0 15:21:22        2
2002:ABCD:EEBB:FFFF:A::2
                4         2042    1013    1014       15    0    0 15:11:45        2
```
### ***Настроите eBGP между офисом С.-Петербург и провайдером Триада***

**R18**

```
R18>en
R18#conf t
R18(config)#router bgp 2042
R18(config-router)#bgp router-id 18.18.18.18
R18(config-router)#network 109.72.1.36 mask 255.255.255.252
R18(config-router)#network 109.72.1.40 mask 255.255.255.252
R18(config-router)#neighbor 109.72.1.37 remote-as 520
R18(config-router)#neighbor 109.72.1.41 remote-as 520

R18#sh ip bgp summary

Neighbor        V           AS MsgRcvd MsgSent   TblVer  InQ OutQ Up/Down  State/PfxRcd
109.72.1.37     4          520     113     113       28    0    0 01:28:21       5
109.72.1.41     4          520     111     112       28    0    0 01:28:08       5
```

### ***Организуете IP доступность между пограничным роутерами офисами Москва и С.-Петербург***

**R14**

```
R14#ping 109.72.1.38
Type escape sequence to abort.
Sending 5, 100-byte ICMP Echos to 109.72.1.38, timeout is 2 seconds:
!!!!!
Success rate is 100 percent (5/5), round-trip min/avg/max = 1/1/2 ms
```
```
R14#ping 109.72.1.42
Type escape sequence to abort.
Sending 5, 100-byte ICMP Echos to 109.72.1.42, timeout is 2 seconds:
!!!!!
Success rate is 100 percent (5/5), round-trip min/avg/max = 1/1/1 ms
```

**R15**

```
R15#ping 109.72.1.38
Type escape sequence to abort.
Sending 5, 100-byte ICMP Echos to 109.72.1.38, timeout is 2 seconds:
!!!!!
Success rate is 100 percent (5/5), round-trip min/avg/max = 1/1/1 ms
```
```
R15#ping 109.72.1.42
Type escape sequence to abort.
Sending 5, 100-byte ICMP Echos to 109.72.1.42, timeout is 2 seconds:
!!!!!
Success rate is 100 percent (5/5), round-trip min/avg/max = 1/1/2 ms
```

**R18**

```
R18#ping 82.138.2.2
Type escape sequence to abort.
Sending 5, 100-byte ICMP Echos to 82.138.2.2, timeout is 2 seconds:
!!!!!
Success rate is 100 percent (5/5), round-trip min/avg/max = 1/1/2 ms
```
```
R18#ping 77.94.165.2
Type escape sequence to abort.
Sending 5, 100-byte ICMP Echos to 77.94.165.2, timeout is 2 seconds:
!!!!!
Success rate is 100 percent (5/5), round-trip min/avg/max = 1/1/2 ms
```
