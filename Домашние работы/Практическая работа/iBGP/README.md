# Задание

#### Настроите iBGP в офисом Москва между маршрутизаторами R14 и R15
#### Настроите iBGP в провайдере Триада, с использованием RR.
#### Настройте офиса Москва так, чтобы приоритетным провайдером стал Ламас.
#### Настройте офиса С.-Петербург так, чтобы трафик до любого офиса распределялся по двум линкам одновременно.
#### Все сети в лабораторной работе должны иметь IP связность.

## Схема сети
![iBGP](https://user-images.githubusercontent.com/112701413/206242319-ddac228f-cd39-4130-838b-684ac47aff77.jpg)


### Настроите iBGP в офисом Москва между маршрутизаторами R14 и R15
### Настройте офиса Москва так, чтобы приоритетным провайдером стал Ламас

**R14**
```
R14>en
R14#conf t
R14(config)#router bgp 1001
R14(config-router)#neighbor 77.37.144.15 remote-as 1001
R14(config-router)#neighbor 77.37.144.15 update-source loopback 14
R14(config-router)#neighbor 77.37.144.15 next-hop-self
R14(config-router)#network 10.10.1.24 mask 255.255.255.252
````
**R15**
```
R15>en
R15#conf t
R15(config)#route-map ROOT permit 10
R15(config-route-map)#set local-preference 200
R15(config-route-map)#exit
R15(config)#router bgp 1001
R15(config-router)#neighbor 77.37.144.14 remote-as 1001
R15(config-router)#neighbor 77.37.144.14 update-source loopback 15
R15(config-router)#neighbor 77.37.144.14 next-hop-self
R15(config-router)#network 10.10.1.24 mask 255.255.255.252
R15(config-router)#neighbor 77.37.144.14 route-map ROOT out
```
#### **Проверим как ходит трафик**
**R15**
```
R15#traceroute 33.72.66.18
Type escape sequence to abort.
Tracing the route to 33.72.66.18
VRF info: (vrf in name/id, vrf out name/id)
  1 77.94.165.1 1 msec 1 msec 0 msec
  2 109.72.1.21 [AS 301] 1 msec 1 msec 1 msec
  3 109.72.1.38 [AS 520] 1 msec *  1 msec
```
**R14**
```
R14#traceroute 33.72.66.18
Type escape sequence to abort.
Tracing the route to 33.72.66.18
VRF info: (vrf in name/id, vrf out name/id)
  1 10.10.1.26 0 msec 0 msec 1 msec
  2 77.94.165.1 0 msec 1 msec 0 msec
  3 109.72.1.21 [AS 301] 1 msec 1 msec 1 msec
  4 109.72.1.38 [AS 520] 1 msec *  2 msec
```

#### Настроите iBGP в провайдере Триада, с использованием RR
**R24**
```
R24>en
R24#conf t
R24(config)#no ro
R24(config)#no router
R24(config)#no router b
R24(config)#no router bgp 520
R24(config-router)#neighbor RR-CLIENTS peer-group
R24(config-router)#neighbor RR-CLIENTS remote-as 520
R24(config-router)#neighbor RR-CLIENTS update-source loopback 24
R24(config-router)#neighbor RR-CLIENTS soft-reconfiguration inbound
R24(config-router)#neighbor 109.72.255.23 peer-group RR-CLIENTS
R24(config-router)#neighbor 109.72.255.25 peer-group RR-CLIENTS
R24(config-router)#neighbor 109.72.255.26 peer-group RR-CLIENTS
```
**R23**
```
