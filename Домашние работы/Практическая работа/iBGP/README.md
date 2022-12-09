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
R14(config-router)#network 77.37.144.252 mask 255.255.255.252
````
**R15**
```
R15>en
R15#conf t
R15(config)#router bgp 1001
R15(config-router)#neighbor 77.37.144.253 remote-as 1001
R15(config-router)#network 77.37.144.252 mask 255.255.255.252
```
#### Настройте офиса Москва так, чтобы приоритетным провайдером стал Ламас
```
R15>en
R15#conf t
R15(config)#route-map LP permit 10
R15(config-route-map)#set local-preference 200
R15(config-route-map)#exit
R15(config)#router bgp 1001
R15(config-router)#neighbor 77.37.144.253 route-map LP out
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
```
**R23**
```
R23>en
R23#conf t
R23(config)#router bgp 520
R23(config-router)#neighbor 109.72.1.18 remote-as 101
R23(config-router)#neighbor 109.72.255.24 remote-as 520
R23(config-router)#neighbor 109.72.255.24 update-source Loopback23
R23(config-router)#neighbor 109.72.255.24 next-hop-self
R24(config-router)#neighbor 109.72.255.24 soft-reconfiguration inbound
```
**R25**
```
R25>en
R25#conf t
R25(config)#router bgp 520
R25(config-router)#neighbor 109.72.255.24 remote-as 520
R25(config-router)#neighbor 109.72.255.24 update-source Loopback25
R25(config-router)#neighbor 109.72.255.24 next-hop-self
R25(config-router)#neighbor 109.72.255.24 soft-reconfiguration inbound
R25(config-router)#redistribute static
```
**R26**
```
R26>en
R26#conf t
R26(config)#router bgp 520
R26(config-router)#neighbor 109.72.255.24 remote-as 520
R26(config-router)#neighbor 109.72.255.24 update-source Loopback26
R26(config-router)#neighbor 109.72.255.24 next-hop-self
R26(config-router)#neighbor 109.72.255.24 soft-reconfiguration inbound
R26(config-router)#redistribute static
```
