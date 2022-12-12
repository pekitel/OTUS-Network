# Задание

#### Настроите iBGP в офисом Москва между маршрутизаторами R14 и R15
#### Настроите iBGP в провайдере Триада, с использованием RR.
#### Настройте офиса Москва так, чтобы приоритетным провайдером стал Ламас.
#### Настройте офиса С.-Петербург так, чтобы трафик до любого офиса распределялся по двум линкам одновременно.
#### Все сети в лабораторной работе должны иметь IP связность.

## Схема сети

![eBGP](https://user-images.githubusercontent.com/112701413/206730008-42eb3ac3-a97a-4c56-908a-99039386a45f.jpg)


### Настроите iBGP в офисом Москва между маршрутизаторами R14 и R15

**R14**
```
R14>en
R14#conf t
R14(config)#router bgp 1001
R14(config-router)#neighbor 77.37.144.254 remote-as 1001
R14(config-router)#neighbor 2001:ABCD:EEBB:AAAA:7::2 remote-as 1001
R14(config-router)#address-family ipv4 unicast
R14(config-router-af)#neighbor 77.37.144.254 activate
R14(config-router-af)#network 77.37.144.252 mask 255.255.255.252
R14(config-router-af)#exit-address-family
R14(config-router)#address-family ipv6 unicast
R14(config-router-af)#neighbor 2001:ABCD:EEBB:AAAA:7::2 activate
R14(config-router-af)#network 2001:ABCD:EEBB:AAAA:7::0/80
R14(config-router-af)#end
R14#wr
````
**R15**
```
R15>en
R15#conf t
R15(config)#router bgp 1001
R15(config-router)#neighbor 77.37.144.253 remote-as 1001
R15(config-router)#neighbor 2001:ABCD:EEBB:AAAA:7::1 remote-as 1001
R15(config-router)#address-family ipv4 unicast
R15(config-router-af)#neighbor 77.37.144.253 activate
R15(config-router-af)#network 77.37.144.252 mask 255.255.255.252
R15(config-router-af)#exit-address-family
R15(config-router)#address-family ipv6 unicast
R15(config-router-af)#neighbor 2001:ABCD:EEBB:AAAA:7::1 activate
R15(config-router-af)#network 2001:ABCD:EEBB:AAAA:7::0/80
R15(config-router-af)#end
R14#wr
```
#### Настройте офиса Москва так, чтобы приоритетным провайдером стал Ламас
```
R15>en
R15#conf t
R15(config)#route-map LP permit 10
R15(config-route-map)#set local-preference 200
R15(config-route-map)#exit
R15(config)#router bgp 1001
R15(config-router)#address-family ipv4 unicast
R15(config-router-af)#neighbor 77.37.144.253 route-map LP out
R15(config-router-af)#exit-address-family
R15(config-router)#address-family ipv6 unicast
R15(config-router-af)#neighbor 2001:ABCD:EEBB:AAAA:7::1 route-map LP out
R15(config-router-af)#end
R15#wr
```
#### **Проверим как ходит трафик**
**R15**
```
R15#traceroute 109.72.1.38           
Type escape sequence to abort.
Tracing the route to 109.72.1.38
VRF info: (vrf in name/id, vrf out name/id)
  1 77.94.165.1 1 msec 0 msec 0 msec
  2 109.72.1.21 1 msec 0 msec 1 msec
  3 109.72.1.38 [AS 2042] 1 msec *  1 msec
```
```
R15#traceroute 2002:ABCD:EEBB:FFFF:A::2
Type escape sequence to abort.
Tracing the route to 2002:ABCD:EEBB:FFFF:A::2

  1 1999:ABCD:EEBB:FFFF:1::1 0 msec 0 msec 1 msec
  2 2002:ABCD:EEBB:FFFF:9::1 0 msec 1 msec 0 msec
  3 2002:ABCD:EEBB:FFFF:A::2 [AS 2042] 1 msec 1 msec 0 msec

```
**R14**
```
R14#traceroute 109.72.1.38
Type escape sequence to abort.
Tracing the route to 109.72.1.38
VRF info: (vrf in name/id, vrf out name/id)
  1 77.37.144.254 1 msec 0 msec 0 msec
  2 77.94.165.1 1 msec 0 msec 1 msec
  3 109.72.1.21 1 msec 0 msec 1 msec
  4 109.72.1.38 [AS 2042] 1 msec *  2 msec
```
```
R14#traceroute 2002:ABCD:EEBB:FFFF:A::2
Type escape sequence to abort.
Tracing the route to 2002:ABCD:EEBB:FFFF:A::2

  1 2001:ABCD:EEBB:AAAA:7::2 0 msec 1 msec 1 msec
  2 1999:ABCD:EEBB:FFFF:1::1 1 msec 1 msec 0 msec
  3 2002:ABCD:EEBB:FFFF:9::1 2 msec 1 msec 1 msec
  4 2002:ABCD:EEBB:FFFF:A::2 [AS 2042] 2 msec 1 msec 1 msec
```
```
R14#show ip bgp 77.37.144.252/30
BGP routing table entry for 77.37.144.252/30, version 2
Paths: (2 available, best #2, table default)
  Advertised to update-groups:
     1          2         
  Refresh Epoch 1
  Local
    77.37.144.254 from 77.37.144.254 (15.15.15.15)
      Origin IGP, metric 0, localpref 200, valid, internal
  Refresh Epoch 1
  Local
    0.0.0.0 from 0.0.0.0 (14.14.14.14)
      Origin IGP, metric 0, localpref 100, weight 32768, valid, sourced, local, best
```
```
R14#show ip bgp ipv6 unicast 2001:ABCD:EEBB:AAAA:7::0/80
BGP routing table entry for 2001:ABCD:EEBB:AAAA:7::/80, version 2
Paths: (2 available, best #2, table default)
  Advertised to update-groups:
     1          2
  Refresh Epoch 4
  Local
    2001:ABCD:EEBB:AAAA:7::2 from 2001:ABCD:EEBB:AAAA:7::2 (15.15.15.15)
      Origin IGP, metric 0, localpref 200, valid, internal
  Refresh Epoch 1
  Local
    :: from 0.0.0.0 (14.14.14.14)
      Origin IGP, metric 0, localpref 100, weight 32768, valid, sourced, local, best
```
***"Видим что localpref поменялся с 100 на 200 и маршрут через R15 стал приоритетным"***

#### Настроите iBGP в провайдере Триада, с использованием RR
**R24**
```
R24>en
R24#conf t
R24(config)#router bgp 520
R24(config-router)#neighbor RR-CLIENTS peer-group
R24(config-router)#neighbor RR-CLIENTS remote-as 520
R24(config-router)#neighbor RR-CLIENTS update-source loopback 24
R24(config-router)#neighbor RR-CLIENTS route-reflector-client
R24(config-router)#neighbor RR-CLIENTS soft-reconfiguration inbound
R24(config-router)#neighbor 109.72.255.23 peer-group RR-CLIENTS
R24(config-router)#neighbor 109.72.255.25 peer-group RR-CLIENTS
R24(config-router)#neighbor 109.72.255.26 peer-group RR-CLIENTS
R24(config-router)#neighbor 2002:ABCD:EEBB:CCCC::23 remote-as 520
R24(config-router)#neighbor 2002:ABCD:EEBB:CCCC::23 update-source Loopback24
R24(config-router)#neighbor 2002:ABCD:EEBB:CCCC::25 remote-as 520
R24(config-router)#neighbor 2002:ABCD:EEBB:CCCC::25 update-source Loopback24
R24(config-router)#neighbor 2002:ABCD:EEBB:CCCC::26 remote-as 520
R24(config-router)#neighbor 2002:ABCD:EEBB:CCCC::26 update-source Loopback24
R24(config-router)#neighbor 2002:ABCD:EEBB:FFFF:9::2 remote-as 301
R24(config-router)#neighbor 2002:ABCD:EEBB:FFFF:A::2 remote-as 2042
R24(config-router)#address-family ipv4 unicast
R24(config-router-af)#neighbor 109.72.255.23 activate
R24(config-router-af)#neighbor 109.72.255.25 activate
R24(config-router-af)#neighbor 109.72.255.26 activate
R24(config-router-af)#exit-address-family
R24(config-router)#address-family ipv6 unicast
R24(config-router-af)#neighbor 2002:ABCD:EEBB:CCCC::23 activate
R24(config-router-af)#neighbor 2002:ABCD:EEBB:CCCC::23 route-reflector-client
R24(config-router-af)#neighbor 2002:ABCD:EEBB:CCCC::23 next-hop-self
R24(config-router-af)#neighbor 2002:ABCD:EEBB:CCCC::23 soft-reconfiguration inbound
R24(config-router-af)#neighbor 2002:ABCD:EEBB:CCCC::25 activate
R24(config-router-af)#neighbor 2002:ABCD:EEBB:CCCC::25 route-reflector-client
R24(config-router-af)#neighbor 2002:ABCD:EEBB:CCCC::25 next-hop-self
R24(config-router-af)#neighbor 2002:ABCD:EEBB:CCCC::25 soft-reconfiguration inbound
R24(config-router-af)#neighbor 2002:ABCD:EEBB:CCCC::26 activate
R24(config-router-af)#neighbor 2002:ABCD:EEBB:CCCC::26 route-reflector-client
R24(config-router-af)#neighbor 2002:ABCD:EEBB:CCCC::26 next-hop-self
R24(config-router-af)#neighbor 2002:ABCD:EEBB:CCCC::26 soft-reconfiguration inbound
R24(config-router-af)#end
R24#wr
```
**R23**
```
R23>en
R23#conf t
R23(config)#router bgp 520
R23(config-router)#neighbor 109.72.1.18 remote-as 101
R23(config-router)#neighbor 2002:ABCD:EEBB:FFFF:8::2 remote-as 101
R23(config-router)#neighbor 2002:ABCD:EEBB:CCCC::24 update-source Loopback23
R23(config-router)#neighbor 2002:ABCD:EEBB:CCCC::24 remote-as 520
R23(config-router)#neighbor 109.72.255.24 remote-as 520
R23(config-router)#neighbor 109.72.255.24 update-source Loopback23
R23(config-router)#address-family ipv4 unicast
R23(config-router-af)#neighbor 109.72.255.24 activate
R23(config-router-af)#neighbor 109.72.255.24 next-hop-self
R23(config-router-af)#neighbor 109.72.255.24 soft-reconfiguration inbound
R23(config-router-af)#exit-address-family
R23(config-router)#address-family ipv6 unicast
R23(config-router-af)#neighbor 2002:ABCD:EEBB:CCCC::24 activate
R23(config-router-af)#neighbor 2002:ABCD:EEBB:CCCC::24 next-hop-self
R23(config-router-af)#neighbor 2002:ABCD:EEBB:CCCC::24 soft-reconfiguration inbound
R23(config-router-af)#neighbor 2002:ABCD:EEBB:FFFF:8::2 activate
R23(config-router-af)#end
R23#wr
```
**R25**
```
R25>en
R25#conf t
R25(config)#router bgp 520
R25(config-router)#neighbor 109.72.255.24 remote-as 520
R25(config-router)#neighbor 109.72.255.24 update-source Loopback25
R25(config-router)#neighbor 2002:ABCD:EEBB:CCCC::24 remote-as 520
R25(config-router)#neighbor 2002:ABCD:EEBB:CCCC::24 update-source Loopback25
R25(config-router)#address-family ipv4 unicast
R25(config-router-af)#redistribute static
R25(config-router-af)#neighbor 109.72.255.24 activate
R25(config-router-af)#neighbor 109.72.255.24 next-hop-self
R25(config-router-af)#neighbor 109.72.255.24 soft-reconfiguration inbound
R25(config-router-af)#exit-address-family
R25(config-router)#address-family ipv6 unicast
R25(config-router-af)#redistribute static
R25(config-router-af)#neighbor 2002:ABCD:EEBB:CCCC::24 activate
R25(config-router-af)#neighbor 2002:ABCD:EEBB:CCCC::24 next-hop-self
R25(config-router-af)#neighbor 2002:ABCD:EEBB:CCCC::24 soft-reconfiguration inbound
R25(config-router-af)#end
R25#wr
```
**R26**
```
R26>en
R26#conf t
R26(config)#router bgp 520
R26(config-router)#neighbor 109.72.1.42 remote-as 2042
R26(config-router)#neighbor 109.72.255.24 remote-as 520
R26(config-router)#neighbor 109.72.255.24 update-source Loopback26
R26(config-router)#neighbor 2002:ABCD:EEBB:CCCC::24 remote-as 520
R26(config-router)#neighbor 2002:ABCD:EEBB:CCCC::24 update-source Loopback26
R26(config-router)#neighbor 2002:ABCD:EEBB:FFFF:B::2 remote-as 2042
R26(config-router)#address-family ipv4 unicast
R26(config-router-af)#neighbor 109.72.255.24 activate
R26(config-router-af)#neighbor 109.72.255.24 next-hop-self
R26(config-router-af)#neighbor 109.72.255.24 soft-reconfiguration inbound
R26(config-router-af)#neighbor 109.72.1.42 activate
R26(config-router-af)#redistribute static
R26(config-router-af)#exit-address-family
R26(config-router)#address-family ipv6 unicast
R26(config-router-af)#redistribute static
R26(config-router-af)#neighbor 2002:ABCD:EEBB:CCCC::24 activate
R26(config-router-af)#neighbor 2002:ABCD:EEBB:CCCC::24 next-hop-self
R26(config-router-af)#neighbor 2002:ABCD:EEBB:CCCC::24 soft-reconfiguration inbound
R26(config-router-af)#neighbor 2002:ABCD:EEBB:FFFF:B::2 activate
R26(config-router-af)#end
R26#wr
```
#### Настройте офиса С.-Петербург так, чтобы трафик до любого офиса распределялся по двум линкам одновременно.
**R18**
```
R18>en
R18#conf t
R18(config)#router bgp 2042
R18(config-router)#address-family ipv4 unicast
R18(config-router-af)#maximum-paths 2
R18(config-router-af)#exit-address-family
R18(config-router)#address-family ipv6 unicast
R18(config-router-af)#maximum-paths 2
R18(config-router-af)#end
R18#wr
```
***Проверим***
```
R18#traceroute 82.138.2.2
Type escape sequence to abort.
Tracing the route to 82.138.2.2
VRF info: (vrf in name/id, vrf out name/id)
  1 109.72.1.37 1 msec
    109.72.1.41 0 msec
    109.72.1.37 1 msec
  2 109.72.1.10 0 msec
    109.72.1.22 1 msec
    109.72.1.10 1 msec
  3 77.94.165.2 [AS 1001] 0 msec
    109.72.1.22 1 msec
    77.94.165.2 [AS 1001] 1 msec
  4 77.94.165.2 [AS 1001] 1 msec
    77.37.144.253 [AS 1001] 1 msec
    77.94.165.2 [AS 1001] 1 msec
```
```
R18#traceroute 2000:ABCD:EEBB:FFFF:1::2
Type escape sequence to abort.
Tracing the route to 2000:ABCD:EEBB:FFFF:1::2

  1 2002:ABCD:EEBB:FFFF:A::1 1 msec
    2002:ABCD:EEBB:FFFF:B::1 0 msec
    2002:ABCD:EEBB:FFFF:A::1 1 msec
  2 2002:ABCD:EEBB:FFFF:6::2 0 msec
    2002:ABCD:EEBB:FFFF:9::2 1 msec
    2002:ABCD:EEBB:FFFF:6::2 0 msec
  3 1999:ABCD:EEBB:FFFF:1::2 [AS 1001] 1 msec
    2002:ABCD:EEBB:FFFF:9::2 0 msec
    1999:ABCD:EEBB:FFFF:1::2 1 msec
  4 1999:ABCD:EEBB:FFFF:1::2 [AS 1001] 1 msec
    2001:ABCD:EEBB:AAAA:7::1 1 msec
    1999:ABCD:EEBB:FFFF:1::2 1 msec
```
