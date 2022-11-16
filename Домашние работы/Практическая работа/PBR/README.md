# Задание

1. [Настроите политику маршрутизации для сетей офиса](https://github.com/pekitel/OTUS-Network/blob/main/%D0%94%D0%BE%D0%BC%D0%B0%D1%88%D0%BD%D0%B8%D0%B5%20%D1%80%D0%B0%D0%B1%D0%BE%D1%82%D1%8B/%D0%9F%D1%80%D0%B0%D0%BA%D1%82%D0%B8%D1%87%D0%B5%D1%81%D0%BA%D0%B0%D1%8F%20%D1%80%D0%B0%D0%B1%D0%BE%D1%82%D0%B0/PBR/README.md#%D0%BD%D0%B0%D1%81%D1%82%D1%80%D0%BE%D0%B9%D0%BA%D0%B0-%D0%BF%D0%BE%D0%BB%D0%B8%D1%82%D0%B8%D0%BA%D0%B8-%D0%BC%D0%B0%D1%80%D1%88%D1%80%D1%83%D1%82%D0%B8%D0%B7%D0%B0%D1%86%D0%B8%D0%B8-%D0%B4%D0%BB%D1%8F-%D1%81%D0%B5%D1%82%D0%B5%D0%B9-%D0%BE%D1%84%D0%B8%D1%81%D0%B0) 
2. [Распределите трафик между двумя линками с провайдером](https://github.com/pekitel/OTUS-Network/blob/main/%D0%94%D0%BE%D0%BC%D0%B0%D1%88%D0%BD%D0%B8%D0%B5%20%D1%80%D0%B0%D0%B1%D0%BE%D1%82%D1%8B/%D0%9F%D1%80%D0%B0%D0%BA%D1%82%D0%B8%D1%87%D0%B5%D1%81%D0%BA%D0%B0%D1%8F%20%D1%80%D0%B0%D0%B1%D0%BE%D1%82%D0%B0/PBR/README.md#%D1%80%D0%B0%D1%81%D0%BF%D1%80%D0%B5%D0%B4%D0%B5%D0%BB%D0%B5%D0%BD%D0%B8%D0%B5-%D1%82%D1%80%D0%B0%D1%84%D0%B8%D0%BA%D0%B0-%D0%BC%D0%B5%D0%B6%D0%B4%D1%83-%D0%B4%D0%B2%D1%83%D0%BC%D1%8F-%D0%BB%D0%B8%D0%BD%D0%BA%D0%B0%D0%BC%D0%B8-%D1%81-%D0%BF%D1%80%D0%BE%D0%B2%D0%B0%D0%B9%D0%B4%D0%B5%D1%80%D0%BE%D0%BC)
3. [Настроите отслеживание линка через технологию IP SLA.(только для IPv4)](https://github.com/pekitel/OTUS-Network/blob/main/%D0%94%D0%BE%D0%BC%D0%B0%D1%88%D0%BD%D0%B8%D0%B5%20%D1%80%D0%B0%D0%B1%D0%BE%D1%82%D1%8B/%D0%9F%D1%80%D0%B0%D0%BA%D1%82%D0%B8%D1%87%D0%B5%D1%81%D0%BA%D0%B0%D1%8F%20%D1%80%D0%B0%D0%B1%D0%BE%D1%82%D0%B0/PBR/README.md#%D0%BD%D0%B0%D1%81%D1%82%D1%80%D0%BE%D0%B8%D1%82%D0%B5-%D0%BE%D1%82%D1%81%D0%BB%D0%B5%D0%B6%D0%B8%D0%B2%D0%B0%D0%BD%D0%B8%D0%B5-%D0%BB%D0%B8%D0%BD%D0%BA%D0%B0-%D1%87%D0%B5%D1%80%D0%B5%D0%B7-%D1%82%D0%B5%D1%85%D0%BD%D0%BE%D0%BB%D0%BE%D0%B3%D0%B8%D1%8E-ip-sla%D1%82%D0%BE%D0%BB%D1%8C%D0%BA%D0%BE-%D0%B4%D0%BB%D1%8F-ipv4)
4. [Настройте для офиса Лабытнанги маршрут по-умолчанию](https://github.com/pekitel/OTUS-Network/blob/main/%D0%94%D0%BE%D0%BC%D0%B0%D1%88%D0%BD%D0%B8%D0%B5%20%D1%80%D0%B0%D0%B1%D0%BE%D1%82%D1%8B/%D0%9F%D1%80%D0%B0%D0%BA%D1%82%D0%B8%D1%87%D0%B5%D1%81%D0%BA%D0%B0%D1%8F%20%D1%80%D0%B0%D0%B1%D0%BE%D1%82%D0%B0/PBR/README.md#%D0%BD%D0%B0%D1%81%D1%82%D1%80%D0%BE%D0%B9%D1%82%D0%B5-%D0%B4%D0%BB%D1%8F-%D0%BE%D1%84%D0%B8%D1%81%D0%B0-%D0%BB%D0%B0%D0%B1%D1%8B%D1%82%D0%BD%D0%B0%D0%BD%D0%B3%D0%B8-%D0%BC%D0%B0%D1%80%D1%88%D1%80%D1%83%D1%82-%D0%BF%D0%BE-%D1%83%D0%BC%D0%BE%D0%BB%D1%87%D0%B0%D0%BD%D0%B8%D1%8E)

## Схема сети

>![PBR_ipv4](https://user-images.githubusercontent.com/112701413/202274467-1f0527a8-042b-4b28-81fa-67309ef7fd17.jpg)




| Hosts     | Port    | IPv4             | IPv6                           | Примечание      | Регион     |
|:---------:|:-------:|:----------------:|:------------------------------:|:---------------:|:----------:|
| R27       | e0/0    | 109.72.1.26/30   | 2002:ABCD:EEBB:FFFF:3::2/80    | R25(Triada)     | Лабытнанги |
| R28       | e0/0    | 109.72.1.34/30   | 2002:ABCD:EEBB:FFFF:4::2/80    | R26(Triada)     | Чокурдах   |
|           | e0/1    | 109.72.1.30/30   | 2002:ABCD:EEBB:FFFF:2::2/80    | R25(Triada)     |            |
|           | e0/2.10 | 172.16.2.1/28    | 2002:ABCD:EEBB:AAAA:2222::1/80 | SW29(Chukordah) |            |
|           | e0/2.20 | 172.16.2.17/28   | 2002:ABCD:EEBB:AAAA:3333::1/80 | SW29(Chukordah) |            |
| VPC30     |         | 172.16.2.2/28    | 2002:ABCD:EEBB:AAAA:2222::2/80 |                 |            |
| VPC31     |         | 172.16.2.18/28  | 2002:ABCD:EEBB:AAAA:3333::2/80 |                 |            |


#### Настройка политики маршрутизации для сетей офиса

**R28**

```
R28#show ipv6 int brief
Ethernet0/0            [up/up]
    FE80::28
    2002:ABCD:EEBB:FFFF:4::2
Ethernet0/1            [up/up]
    FE80::28
    2002:ABCD:EEBB:FFFF:2::2
Ethernet0/2            [up/up]
    unassigned
Ethernet0/2.10         [up/up]
    FE80::28
    2002:ABCD:EEBB:AAAA:2222::1
Ethernet0/2.20         [up/up]
    FE80::28
    2002:ABCD:EEBB:AAAA:3333::1
Ethernet0/2.99         [up/up]
    FE80::28
    2002:ABCD:EEBB:AAAA:1111::1
Ethernet0/2.777        [up/up]
    unassigned
```

```
R28#show ip int brief
Interface                  IP-Address      OK? Method Status                Protocol
Ethernet0/0                109.72.1.34     YES NVRAM  up                    up      
Ethernet0/1                109.72.1.30     YES NVRAM  up                    up      
Ethernet0/2.10             172.16.2.1      YES manual up                    up      
Ethernet0/2.20             172.16.2.17     YES manual up                    up      
Ethernet0/2.99             172.16.20.1     YES manual up                    up      
Ethernet0/2.777            unassigned      YES unset  up                    up      
Loopback28                 109.72.67.28    YES manual up                    up 
```

**R25**

```
R25#show ipv6 int brief 
Ethernet0/0            [up/up]
    FE80::25
    2002:ABCD:EEBB:FFFF:1::2
Ethernet0/1            [up/up]
    FE80::25
    2002:ABCD:EEBB:FFFF:3::1
Ethernet0/2            [up/up]
    FE80::25
    2002:ABCD:EEBB:FFFF:5::2
Ethernet0/3            [up/up]
    FE80::25
    2002:ABCD:EEBB:FFFF:2::1
Loopback25             [up/up]
    FE80:1::25
```
```
R25#show ip int brief   
Interface                  IP-Address      OK? Method Status                Protocol
Ethernet0/0                109.72.1.2      YES NVRAM  up                    up      
Ethernet0/1                109.72.1.25     YES NVRAM  up                    up      
Ethernet0/2                109.72.1.5      YES NVRAM  up                    up      
Ethernet0/3                109.72.1.29     YES NVRAM  up                    up      
Loopback25                 109.72.255.25   YES NVRAM  up                    up      
```


**R26**

```
R26#show ipv6 int brief 
Ethernet0/0            [up/up]
    FE80::26
    2002:ABCD:EEBB:FFFF:6::1
Ethernet0/1            [up/up]
    FE80::26
    2002:ABCD:EEBB:FFFF:4::1
Ethernet0/2            [up/up]
    FE80::26
    2002:ABCD:EEBB:FFFF:5::1
Ethernet0/3            [up/up]
    FE80::26
    2002:ABCD:EEBB:FFFF:B::1
Loopback26             [up/up]
    FE80:1::26
```
```
R26#show ip int brief   
Interface                  IP-Address      OK? Method Status                Protocol
Ethernet0/0                109.72.1.9      YES NVRAM  up                    up      
Ethernet0/1                109.72.1.33     YES NVRAM  up                    up      
Ethernet0/2                109.72.1.6      YES NVRAM  up                    up      
Ethernet0/3                109.72.1.41     YES NVRAM  up                    up      
Loopback26                 109.72.255.26   YES NVRAM  up                    up  
```

#### Распределение трафика между двумя линками с провайдером

**R28**
```
ip route 0.0.0.0 0.0.0.0 109.72.1.29
ip route 0.0.0.0 0.0.0.0 109.72.1.33
ipv6 route ::/0 2002:ABCD:EEBB:FFFF:2::1
ipv6 route ::/0 2002:ABCD:EEBB:FFFF:4::1

ip access-list extended ACL1
 permit ip host 172.16.2.2 any

route-map VPC30 permit 10
 match ip address ACL1
 set ip next-hop 109.72.1.33
 set ipv6 next-hop 2002:ABCD:EEBB:FFFF:4::1
 
interface Ethernet0/2
 ip policy route-map VPC30
 ```
 
 #### Настроите отслеживание линка через технологию IP SLA.(только для IPv4)
 ```
ip sla 1
 icmp-echo 109.72.1.30 source-interface Ethernet0/1
 frequency 5
ip sla schedule 1 life forever start-time now
ip sla 2
 icmp-echo 109.72.1.34 source-interface Ethernet0/0
 frequency 5
ip sla schedule 2 life forever start-time now
ip route 0.0.0.0 0.0.0.0 109.72.1.29 track 1
ip route 0.0.0.0 0.0.0.0 109.72.1.33 track 2

Поправим route-map чтобы была прорверка линка

route-map VPC30 permit 10
 match ip address ACL1
 set ip next-hop verify-availability 109.72.1.29 10 track 1
 set ip next-hop verify-availability 109.72.1.33 15 track 2
 ```
 Проверка Track и Route-map
 ```
R28#show track 1
Track 1
  IP SLA 1 reachability
  Reachability is Up
    2 changes, last change 1d23h
  Latest operation return code: OK
  Latest RTT (millisecs) 1
  Tracked by:
    Route Map 0
    Static IP Routing 0
R28#show track 2
Track 2
  IP SLA 2 reachability
  Reachability is Up
    2 changes, last change 1d23h
  Latest operation return code: OK
  Latest RTT (millisecs) 1
  Tracked by:
    Route Map 0
    Static IP Routing 0
    
R28#show route-map 
route-map VPC30, permit, sequence 10
  Match clauses:
    ip address (access-lists): ACL1 
  Set clauses:
    ip next-hop verify-availability 109.72.1.29 10 track 1  [up]
    ip next-hop verify-availability 109.72.1.33 15 track 2  [up]
     ipv6 next-hop 2002:ABCD:EEBB:FFFF:2::1
  Policy routing matches: 0 packets, 0 bytes
  ```
  
  #### Настройте для офиса Лабытнанги маршрут по-умолчанию
  
```
R27#sh run | s rout
 ipv6 unicast-routing
 ip route 0.0.0.0 0.0.0.0 109.72.1.25
 ipv6 route ::/0 2002:ABCD:EEBB:FFFF:3::1
```
