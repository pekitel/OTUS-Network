# Задание

### Настроите eBGP между офисом Москва и двумя провайдерами - Киторн и Ламас.
### Настроите eBGP между провайдерами Киторн и Ламас.
### Настроите eBGP между Ламас и Триада.
### Настроите eBGP между офисом С.-Петербург и провайдером Триада.
### Организуете IP доступность между пограничным роутерами офисами Москва и С.-Петербург.

## Карта сети

![eBGP](https://user-images.githubusercontent.com/112701413/206729861-52e52891-6fe1-41f1-ae40-3c513aca7772.jpg)


### ***Настроите eBGP между офисом Москва и двумя провайдерами - Киторн и Ламас*** 
### ***Настроите eBGP между провайдерами Киторн и Ламас*** 

**R14**

```
R14>en
R14#conf t
R14(config)#router bgp 1001
R14(config-router)#bgp router-id 14.14.14.14
R14(config-router)#network 82.138.2.0 mask 255.255.255.252
R14(config-router)#neighbor 82.138.2.1 remote-as 101

R14#show ip bgp summary

Neighbor        V           AS MsgRcvd MsgSent   TblVer  InQ OutQ Up/Down  State/PfxRcd
82.138.2.1      4          101     128     122       33    0    0 01:34:52        0
```

**R15**

```
R15>en
R15#conf t
R15(config)#router bgp 1001
R15(config-router)#bgp router-id 15.15.15.15
R15(config-router)#network 77.94.165.0 mask 255.255.255.252
R15(config-router)#neighbor 77.94.165.1 remote-as 301

R15#show ip bgp summary

Neighbor        V           AS MsgRcvd MsgSent   TblVer  InQ OutQ Up/Down  State/PfxRcd
77.94.165.1     4          301     158     148    19851    0    0 01:49:12        0
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

R21#show ip bgp summary

Neighbor        V           AS MsgRcvd MsgSent   TblVer  InQ OutQ Up/Down  State/PfxRcd
77.94.165.2     4         1001      49      63       27    0    0 00:35:54        2
82.138.2.5      4          101      40      35       27    0    0 00:09:24        5
109.72.1.21     4          520      59      56       27    0    0 00:35:53        4
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

R22#sh ip bgp summary

Neighbor        V           AS MsgRcvd MsgSent   TblVer  InQ OutQ Up/Down  State/PfxRcd
82.138.2.2      4         1001      51      59      226    0    0 00:33:21        2
82.138.2.6      4          301      34      39      226    0    0 00:08:50        5
109.72.1.17     4          520      24      32      226    0    0 00:08:35        4
```

### ***Настроите eBGP между Ламас и Триада (Ну и в Триаде настроим iBGP)*** 

**R23**

```
R23>en
R23#conf t
R23(config)#router bgp 520
R23(config-router)#bgp router-id 23.23.23.23
R23(config-router)#neighbor 109.72.1.18 remote-as 101
R23(config-router)#neighbor 109.72.255.24 remote-as 520
R23(config-router)#neighbor 109.72.255.24 update-source Loopback23
R23(config-router)#neighbor 109.72.255.24 next-hop-self
R23(config-router)#neighbor 109.72.255.24 soft-reconfiguration inbound
R23(config-router)#neighbor 109.72.255.25 remote-as 520
R23(config-router)#neighbor 109.72.255.25 update-source Loopback23
R23(config-router)#neighbor 109.72.255.25 next-hop-self
R23(config-router)#neighbor 109.72.255.25 soft-reconfiguration inbound
R23(config-router)#neighbor 109.72.255.26 remote-as 520
R23(config-router)#neighbor 109.72.255.26 update-source Loopback23
R23(config-router)#neighbor 109.72.255.26 next-hop-self
R23(config-router)#neighbor 109.72.255.26 soft-reconfiguration inbound

R23#show ip bgp summary

Neighbor        V           AS MsgRcvd MsgSent   TblVer  InQ OutQ Up/Down  State/PfxRcd
109.72.1.18     4          101      30      22       15    0    0 00:13:49       10
109.72.255.24   4          520      26      21       15    0    0 00:13:49        9
109.72.255.25   4          520      21      21       15    0    0 00:13:49        2
109.72.255.26   4          520      22      21       15    0    0 00:13:49        2
```

**R24**

```
R24>en
R24#conf t
R24(config)#router bgp 520
R24(config-router)#bgp router-id 24.24.24.24
R24(config-router)#neighbor 109.72.1.22 remote-as 301
R24(config-router)#neighbor 109.72.255.23 remote-as 520
R24(config-router)#neighbor 109.72.255.23 update-source Loopback24
R24(config-router)#neighbor 109.72.255.23 next-hop-self
R24(config-router)#neighbor 109.72.255.23 soft-reconfiguration inbound
R24(config-router)#neighbor 109.72.255.25 remote-as 520
R24(config-router)#neighbor 109.72.255.25 update-source Loopback24
R24(config-router)#neighbor 109.72.255.25 next-hop-self
R24(config-router)#neighbor 109.72.255.25 soft-reconfiguration inbound
R24(config-router)#neighbor 109.72.255.26 remote-as 520
R24(config-router)#neighbor 109.72.255.26 update-source Loopback24
R24(config-router)#neighbor 109.72.255.26 next-hop-self
R24(config-router)#neighbor 109.72.255.26 soft-reconfiguration inbound
R24(config-router)#neighbor 109.72.1.38 remote-as 2042

R24#show ip bgp summary

Neighbor        V           AS MsgRcvd MsgSent   TblVer  InQ OutQ Up/Down  State/PfxRcd
109.72.1.21     4          520      59      56       27    0    0 00:35:53        4
109.72.1.38     4         2042     196     194       64    0    0 02:33:32        1
109.72.255.23   4          520      42      48       27    0    0 00:32:21        8
109.72.255.25   4          520      83      91       27    0    0 01:12:38        2
109.72.255.26   4          520     160     168       27    0    0 02:19:38        5
```

**R25**

```
R25>en
R25#conf t
R25(config)#router bgp 520
R25(config-router)#bgp router-id 25.25.25.25
R25(config-router)#redistribute static
R25(config-router)#neighbor 109.72.255.23 remote-as 520
R25(config-router)#neighbor 109.72.255.23 update-source Loopback25
R25(config-router)#neighbor 109.72.255.23 next-hop-self
R25(config-router)#neighbor 109.72.255.23 soft-reconfiguration inbound
R25(config-router)#neighbor 109.72.255.24 remote-as 520
R25(config-router)#neighbor 109.72.255.24 update-source Loopback25
R25(config-router)#neighbor 109.72.255.24 next-hop-self
R25(config-router)#neighbor 109.72.255.24 soft-reconfiguration inbound
R25(config-router)#neighbor 109.72.255.26 remote-as 520
R25(config-router)#neighbor 109.72.255.26 update-source Loopback25
R25(config-router)#neighbor 109.72.255.26 next-hop-self
R25(config-router)#neighbor 109.72.255.26 soft-reconfiguration inbound

R25#show ip bgp summary

Neighbor        V           AS MsgRcvd MsgSent   TblVer  InQ OutQ Up/Down  State/PfxRcd
109.72.255.23   4          520      44      42       38    0    0 00:33:59        8
109.72.255.24   4          520      93      85       38    0    0 01:14:17       12
109.72.255.26   4          520      89      85       38    0    0 01:14:11        5
```

**26**

```
R26>en
R26#conf t
R26(config)#router bgp 520
R26(config-router)#bgp router-id 26.26.26.26
R26(config-router)#redistribute static
R26(config-router)#neighbor 109.72.1.42 remote-as 2042
R26(config-router)#neighbor 109.72.255.23 remote-as 520
R26(config-router)#neighbor 109.72.255.23 update-source Loopback26
R26(config-router)#neighbor 109.72.255.23 next-hop-self
R26(config-router)#neighbor 109.72.255.23 soft-reconfiguration inbound
R26(config-router)#neighbor 109.72.255.24 remote-as 520
R26(config-router)#neighbor 109.72.255.24 update-source Loopback26
R26(config-router)#neighbor 109.72.255.24 next-hop-self
R26(config-router)#neighbor 109.72.255.24 soft-reconfiguration inbound
R26(config-router)#neighbor 109.72.255.25 remote-as 520
R26(config-router)#neighbor 109.72.255.25 update-source Loopback26
R26(config-router)#neighbor 109.72.255.25 next-hop-self
R26(config-router)#neighbor 109.72.255.25 soft-reconfiguration inbound

R26#show ip bgp summary

Neighbor        V           AS MsgRcvd MsgSent   TblVer  InQ OutQ Up/Down  State/PfxRcd
109.72.1.42     4         2042      76      76       29    0    0 00:56:38        5
109.72.255.23   4          520      51      54       29    0    0 00:41:36        8
109.72.255.24   4          520     178     171       29    0    0 02:28:54       12
109.72.255.25   4          520      93      98       29    0    0 01:21:48        2
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
