# Задание

## Настроить OSPF офисе Москва Разделить сеть на зоны Настроить фильтрацию между зонами

**1. Маршрутизаторы R14-R15 находятся в зоне 0 - backbone**

**2. Маршрутизаторы R12-R13 находятся в зоне 10. Дополнительно к маршрутам должны получать маршрут по-умолчанию**

**3. Маршрутизатор R19 находится в зоне 101 и получает только маршрут по умолчанию**

**4. Маршрутизатор R20 находится в зоне 102 и получает все маршруты, кроме маршрутов до сетей зоны 101**


### Схема сети

>![OSPF](https://user-images.githubusercontent.com/112701413/204143557-0a544dfd-3f3e-481e-8fc8-53ec58c0f11d.jpg)


**Таблица ip адресов**
| Hosts      | Ports    | Network IPv4    | Network IPv6                   | link-local |    Description    | Loopback ipv4 | Loopback ipv6 |
|:----------:|:--------:|:---------------:|:------------------------------:|:----------:|:-----------------:|:-------------:|:-------------:|
| R14        | e0/0     | 10.10.1.5/30    | 2001:ABCD:EEBB:AAAA:2::1/80    | FE80::14   | to --> R12        | 77.37.144.14  | FE80:1::14    |
|            | e0/1     | 10.10.1.9/30    | 2001:ABCD:EEBB:AAAA:3::1/80    | FE80::14   | to --> R13        |               |               |
|            | e0/2     | 82.138.2.2/30   | 2000:ABCD:FFBB:FFFF:1::2/80    | FE80::14   | to --> R22 Kitorn |               |               |
|            | e0/3     | 10.10.1.1/30    | 2001:ABCD:EEBB:AAAA:1::1/80    | FE80::14   | to --> R19        |               |               |
| R15        | e0/0     | 10.10.1.17/30   | 2001:ABCD:EEBB:AAAA:5::1/80    | FE80::15   | to --> R13        | 77.37.144.15  | FE80:1::15    |
|            | e0/1     | 10.10.1.13/30   | 2001:ABCD:EEBB:AAAA:4::1/80    | FE80::15   | to --> R12        |               |               |
|            | e0/2     | 77.94.165.2/30  | 1999:ABCD:EEBB:FFFF:1::2/80    | FE80::15   | to --> R21 Lamas  |               |               |
|            | e0/3     | 10.10.1.21/30   | 2001:ABCD:EEBB:AAAA:6::1/80    | FE80::15   | to --> R20        |               |               |
| R19        | e0/0     | 10.10.1.2/30    | 2001:ABCD:EEBB:AAAA:1::2/80    | FE80::19   | to --> R14        | 77.37.144.19  | FE80:1::19    |
| R12        | e0/2     | 10.10.1.6/30    | 2001:ABCD:EEBB:AAAA:2::2/80    | FE80::12   | to --> R14        | 77.37.144.12  | FE80:1::12    |
|            | e0/3     | 10.10.1.14/30   | 2001:ABCD:EEBB:AAAA:4::2/80    | FE80::12   | to --> R15        |               |               |
|            | e0/0.10  | 172.16.3.1/28   | 2001:ABCD:EEBB:AAAA:2222::1/80 | FE80::12   | to --> SW4        |               |               |
|            | e0/0.20  | 172.16.3.17/25  | 2001:ABCD:EEBB:AAAA:3333::1/80 | FE80::12   | to --> SW4        |               |               |
| R13        | e0/2     | 10.10.1.18/30   | 2001:ABCD:EEBB:AAAA:5::2/80    | FE80::13   | to --> R15        | 77.37.144.13  | FE80:1::13    |
|            | e0/3     | 10.10.1.10/30   | 2001:ABCD:EEBB:AAAA:3::2/80    | FE80::13   | to --> R14        |               |               |
|            | e0/0.99  | 172.16.30.1/29  | 2001:ABCD:EEBB:AAAA:1111::1/80 | FE80::13   | to --> SW5 MGMT   |               |               |
| R20        | e0/0     | 10.10.1.22/30   | 2001:ABCD:EEBB:AAAA:6::2/80    | FE80::20   | to --> R15        | 77.37.144.20  | FE80:1::20    |



**1. Маршрутизаторы R14-R15 находятся в зоне 0 - backbone**

**R14**

```
interface Loopback14
 ip address 77.37.144.14 255.255.255.255
 ipv6 address FE80:1::14 link-local
 ipv6 enable
 ipv6 ospf 1 area 0
!
interface Ethernet0/0
 description to --> R12
 ip address 10.10.1.5 255.255.255.252
 ipv6 address FE80::14 link-local
 ipv6 address 2001:ABCD:EEBB:AAAA:2::1/80
 ipv6 enable
 ipv6 ospf 1 area 0
!
interface Ethernet0/1
 description to --> R13
 ip address 10.10.1.9 255.255.255.252
 ipv6 address FE80::14 link-local
 ipv6 address 2001:ABCD:EEBB:AAAA:3::1/80
 ipv6 enable
 ipv6 ospf 1 area 0
!
interface Ethernet0/2
 description to --> R22
 ip address 82.138.2.2 255.255.255.252
 ipv6 address FE80::14 link-local
 ipv6 address 2000:ABCD:EEBB:FFFF:1::2/80
 ipv6 enable
!
interface Ethernet0/3
 description to --> R19
 ip address 10.10.1.1 255.255.255.252
 ipv6 address FE80::14 link-local
 ipv6 address 2001:ABCD:EEBB:AAAA:1::1/80
 ipv6 enable
 ipv6 ospf 1 area 101
!
router ospf 1
 router-id 14.14.14.14
 area 101 stub no-summary
 network 10.10.1.0 0.0.0.3 area 101
 network 10.10.1.4 0.0.0.3 area 0
 network 10.10.1.8 0.0.0.3 area 0
 network 77.37.144.14 0.0.0.0 area 0
 default-information originate
!
ip route 0.0.0.0 0.0.0.0 82.138.2.1
!
ipv6 route ::/0 2000:ABCD:EEBB:FFFF:1::1
ipv6 router ospf 1
 router-id 14.14.14.14
 area 101 stub no-summary
 
 ```
 **R15**
 ```
 interface Loopback15
 ip address 77.37.144.15 255.255.255.255
 ipv6 address FE80:1::15 link-local
 ipv6 enable
 ipv6 ospf 1 area 0
!
interface Ethernet0/0
 description to --> R13
 ip address 10.10.1.17 255.255.255.252
 ipv6 address FE80::15 link-local
 ipv6 address 2001:ABCD:EEBB:AAAA:5::1/80
 ipv6 enable
 ipv6 ospf 1 area 0
!
interface Ethernet0/1
 description to --> R12
 ip address 10.10.1.13 255.255.255.252
 ipv6 address FE80::15 link-local
 ipv6 address 2001:ABCD:EEBB:AAAA:4::1/80
 ipv6 enable
 ipv6 ospf 1 area 0
!
interface Ethernet0/2
 description to --> R21
 ip address 77.94.165.2 255.255.255.252
 ipv6 address FE80::15 link-local
 ipv6 address 1999:ABCD:EEBB:FFFF:1::2/80
 ipv6 enable
!
interface Ethernet0/3
 description to --> R20
 ip address 10.10.1.21 255.255.255.252
 ipv6 address FE80::15 link-local
 ipv6 address 2001:ABCD:EEBB:AAAA:6::1/80
 ipv6 enable
 ipv6 ospf 1 area 102
!
router ospf 1
 router-id 15.15.15.15
 network 10.10.1.12 0.0.0.3 area 0
 network 10.10.1.16 0.0.0.3 area 0
 network 10.10.1.20 0.0.0.3 area 102
 network 77.37.144.12 0.0.0.3 area 0
 default-information originate
 distribute-list prefix PL1 in
!
ip route 0.0.0.0 0.0.0.0 77.94.165.1
!
ip prefix-list PL1 seq 5 deny 10.10.1.0/30
ip prefix-list PL1 seq 10 permit 0.0.0.0/0 le 32
ipv6 route ::/0 1999:ABCD:EEBB:FFFF:1::1
ipv6 router ospf 1
 router-id 15.15.15.15
 distribute-list prefix-list PL2 in
 default-information originate
!
ipv6 prefix-list PL2 seq 5 deny 2001:ABCD:EEBB:AAAA:1::/80
ipv6 prefix-list PL2 seq 10 permit ::/0 le 128
```

**2. Маршрутизаторы R12-R13 находятся в зоне 10. Дополнительно к маршрутам должны получать маршрут по-умолчанию**

**R12**

```
interface Loopback12
 ip address 77.37.144.12 255.255.255.255
 ipv6 address FE80:1::12 link-local
 ipv6 enable
 ipv6 ospf 1 area 10
!
interface Ethernet0/0
 no ip address
!
interface Ethernet0/0.10
 description to --> VPC1
 encapsulation dot1Q 10
 ip address 172.16.3.1 255.255.255.240
 ip helper-address 10.10.1.5
 ipv6 address FE80::12 link-local
 ipv6 address 2001:ABCD:EEBB:AAAA:2222::1/80
 ipv6 enable
 ipv6 nd managed-config-flag
 ipv6 dhcp relay destination  2001:ABCD:EEBB:AAAA:2::1
 ipv6 ospf 1 area 10
!
interface Ethernet0/0.20
 description to --> VPC7
 encapsulation dot1Q 20
 ip address 172.16.3.17 255.255.255.240
 ip helper-address 10.10.1.5
 ipv6 address FE80::12 link-local
 ipv6 address 2001:ABCD:EEBB:AAAA:3333::1/80
 ipv6 nd managed-config-flag
 ipv6 dhcp relay destination  2001:ABCD:EEBB:AAAA:2::1
 ipv6 ospf 1 area 10
!
interface Ethernet0/1
 no ip address
 shutdown
!
interface Ethernet0/2
 description to --> R14
 ip address 10.10.1.6 255.255.255.252
 ipv6 address FE80::12 link-local
 ipv6 address 2001:ABCD:EEBB:AAAA:2::2/80
 ipv6 enable
 ipv6 ospf 1 area 0
!
interface Ethernet0/3
 description to --> R15
 ip address 10.10.1.14 255.255.255.252
 ipv6 address FE80::12 link-local
 ipv6 address 2001:ABCD:EEBB:AAAA:4::2/80
 ipv6 enable
 ipv6 ospf 1 area 0
!
interface Ethernet1/0
 no ip address
 shutdown
!
interface Ethernet1/1
 no ip address
 shutdown
!
interface Ethernet1/2
 no ip address
 shutdown
!
interface Ethernet1/3
 no ip address
 shutdown
!
router ospf 1
 router-id 12.12.12.12
 network 10.10.1.4 0.0.0.3 area 0
 network 10.10.1.12 0.0.0.3 area 0
 network 77.37.144.12 0.0.0.0 area 10
 network 172.16.3.0 0.0.0.31 area 10
!
ip forward-protocol nd
!
!
no ip http server
no ip http secure-server
!
ipv6 router ospf 1
 router-id 12.12.12.12
```

**R13**

```
interface Loopback13
 ip address 77.37.144.13 255.255.255.255
 ipv6 address FE80:1::13 link-local
 ipv6 ospf 1 area 10
!
interface Ethernet0/0
 no ip address
!
interface Ethernet0/0.99
 encapsulation dot1Q 99
 ip address 172.16.30.1 255.255.255.248
 ipv6 address FE80::13 link-local
 ipv6 address 2001:ABCD:EEBB:AAAA:1111::1/80
 ipv6 enable
 ipv6 ospf 1 area 10
!
interface Ethernet0/0.777
 encapsulation dot1Q 777 native
!
interface Ethernet0/1
 no ip address
 shutdown
!
interface Ethernet0/2
 description to --> R15
 ip address 10.10.1.18 255.255.255.252
 ipv6 address FE80::13 link-local
 ipv6 address 2001:ABCD:EEBB:AAAA:5::2/80
 ipv6 enable
 ipv6 ospf 1 area 0
!
interface Ethernet0/3
 description to --> R14
 ip address 10.10.1.10 255.255.255.252
 ipv6 address FE80::13 link-local
 ipv6 address 2001:ABCD:EEBB:AAAA:3::2/80
 ipv6 enable
 ipv6 ospf 1 area 0
!
interface Ethernet1/0
 no ip address
 shutdown
!
interface Ethernet1/1
 no ip address
 shutdown
!
interface Ethernet1/2
 no ip address
 shutdown
!
interface Ethernet1/3
 no ip address
 shutdown
!
router ospf 1
 router-id 13.13.13.13
 network 10.10.1.8 0.0.0.3 area 0
 network 10.10.1.16 0.0.0.3 area 0
 network 172.16.30.0 0.0.0.7 area 0
!
ip forward-protocol nd
!
!
no ip http server
no ip http secure-server
!
ipv6 router ospf 1
 router-id 13.13.13.13
```

#### Проверим таблицу маршрутизации на R12 и R13

**R12**
```
R12#show ip route ospf
Codes: L - local, C - connected, S - static, R - RIP, M - mobile, B - BGP
       D - EIGRP, EX - EIGRP external, O - OSPF, IA - OSPF inter area
       N1 - OSPF NSSA external type 1, N2 - OSPF NSSA external type 2
       E1 - OSPF external type 1, E2 - OSPF external type 2
       i - IS-IS, su - IS-IS summary, L1 - IS-IS level-1, L2 - IS-IS level-2
       ia - IS-IS inter area, * - candidate default, U - per-user static route
       o - ODR, P - periodic downloaded static route, H - NHRP, l - LISP
       a - application route
       + - replicated route, % - next hop override

Gateway of last resort is 10.10.1.13 to network 0.0.0.0

O*E2  0.0.0.0/0 [110/1] via 10.10.1.13, 11:43:11, Ethernet0/3
                [110/1] via 10.10.1.5, 11:43:11, Ethernet0/2
      10.0.0.0/8 is variably subnetted, 8 subnets, 2 masks
O IA     10.10.1.0/30 [110/20] via 10.10.1.5, 11:43:11, Ethernet0/2
O        10.10.1.8/30 [110/20] via 10.10.1.5, 11:43:11, Ethernet0/2
O        10.10.1.16/30 [110/20] via 10.10.1.13, 11:43:11, Ethernet0/3
O IA     10.10.1.20/30 [110/20] via 10.10.1.13, 11:43:11, Ethernet0/3
      77.0.0.0/32 is subnetted, 5 subnets
O        77.37.144.14 [110/11] via 10.10.1.5, 11:43:11, Ethernet0/2
O        77.37.144.15 [110/11] via 10.10.1.13, 11:43:11, Ethernet0/3
O IA     77.37.144.19 [110/21] via 10.10.1.5, 11:43:11, Ethernet0/2
O IA     77.37.144.20 [110/21] via 10.10.1.13, 11:43:11, Ethernet0/3
      172.16.0.0/16 is variably subnetted, 5 subnets, 3 masks
O        172.16.30.0/29 [110/30] via 10.10.1.13, 11:43:01, Ethernet0/3
                        [110/30] via 10.10.1.5, 11:43:01, Ethernet0/2
R12#show ipv6 route ospf
IPv6 Routing Table - default - 16 entries
Codes: C - Connected, L - Local, S - Static, U - Per-user Static route
       B - BGP, HA - Home Agent, MR - Mobile Router, R - RIP
       H - NHRP, I1 - ISIS L1, I2 - ISIS L2, IA - ISIS interarea
       IS - ISIS summary, D - EIGRP, EX - EIGRP external, NM - NEMO
       ND - ND Default, NDp - ND Prefix, DCE - Destination, NDr - Redirect
       O - OSPF Intra, OI - OSPF Inter, OE1 - OSPF ext 1, OE2 - OSPF ext 2
       ON1 - OSPF NSSA ext 1, ON2 - OSPF NSSA ext 2, la - LISP alt
       lr - LISP site-registrations, ld - LISP dyn-eid, a - Application
OE2 ::/0 [110/1], tag 1
     via FE80::15, Ethernet0/3
     via FE80::14, Ethernet0/2
OI  2001:ABCD:EEBB:AAAA:1::/80 [110/20]
     via FE80::14, Ethernet0/2
O   2001:ABCD:EEBB:AAAA:3::/80 [110/20]
     via FE80::14, Ethernet0/2
O   2001:ABCD:EEBB:AAAA:5::/80 [110/20]
     via FE80::15, Ethernet0/3
OI  2001:ABCD:EEBB:AAAA:6::/80 [110/20]
     via FE80::15, Ethernet0/3
OI  2001:ABCD:EEBB:AAAA:19::19/128 [110/20]
     via FE80::14, Ethernet0/2
OI  2001:ABCD:EEBB:AAAA:1111::/80 [110/30]
     via FE80::15, Ethernet0/3
     via FE80::14, Ethernet0/2
```
**R13**
```
R13#show ip route ospf
Codes: L - local, C - connected, S - static, R - RIP, M - mobile, B - BGP
       D - EIGRP, EX - EIGRP external, O - OSPF, IA - OSPF inter area
       N1 - OSPF NSSA external type 1, N2 - OSPF NSSA external type 2
       E1 - OSPF external type 1, E2 - OSPF external type 2
       i - IS-IS, su - IS-IS summary, L1 - IS-IS level-1, L2 - IS-IS level-2
       ia - IS-IS inter area, * - candidate default, U - per-user static route
       o - ODR, P - periodic downloaded static route, H - NHRP, l - LISP
       a - application route
       + - replicated route, % - next hop override

Gateway of last resort is 10.10.1.17 to network 0.0.0.0

O*E2  0.0.0.0/0 [110/1] via 10.10.1.17, 11:44:36, Ethernet0/2
                [110/1] via 10.10.1.9, 11:44:26, Ethernet0/3
      10.0.0.0/8 is variably subnetted, 8 subnets, 2 masks
O IA     10.10.1.0/30 [110/20] via 10.10.1.9, 11:44:26, Ethernet0/3
O        10.10.1.4/30 [110/20] via 10.10.1.9, 11:44:26, Ethernet0/3
O        10.10.1.12/30 [110/20] via 10.10.1.17, 11:44:36, Ethernet0/2
O IA     10.10.1.20/30 [110/20] via 10.10.1.17, 11:44:36, Ethernet0/2
      77.0.0.0/32 is subnetted, 6 subnets
O IA     77.37.144.12 [110/21] via 10.10.1.17, 11:44:36, Ethernet0/2
                      [110/21] via 10.10.1.9, 11:44:26, Ethernet0/3
O        77.37.144.14 [110/11] via 10.10.1.9, 11:44:26, Ethernet0/3
O        77.37.144.15 [110/11] via 10.10.1.17, 11:44:36, Ethernet0/2
O IA     77.37.144.19 [110/21] via 10.10.1.9, 11:44:26, Ethernet0/3
O IA     77.37.144.20 [110/21] via 10.10.1.17, 11:44:36, Ethernet0/2
      172.16.0.0/16 is variably subnetted, 4 subnets, 3 masks
O IA     172.16.3.0/28 [110/30] via 10.10.1.17, 11:44:36, Ethernet0/2
                       [110/30] via 10.10.1.9, 11:44:26, Ethernet0/3
O IA     172.16.3.16/28 [110/30] via 10.10.1.17, 11:44:36, Ethernet0/2
                        [110/30] via 10.10.1.9, 11:44:26, Ethernet0/3
R13#show ipv6 route ospf
IPv6 Routing Table - default - 15 entries
Codes: C - Connected, L - Local, S - Static, U - Per-user Static route
       B - BGP, HA - Home Agent, MR - Mobile Router, R - RIP
       H - NHRP, I1 - ISIS L1, I2 - ISIS L2, IA - ISIS interarea
       IS - ISIS summary, D - EIGRP, EX - EIGRP external, NM - NEMO
       ND - ND Default, NDp - ND Prefix, DCE - Destination, NDr - Redirect
       O - OSPF Intra, OI - OSPF Inter, OE1 - OSPF ext 1, OE2 - OSPF ext 2
       ON1 - OSPF NSSA ext 1, ON2 - OSPF NSSA ext 2, la - LISP alt
       lr - LISP site-registrations, ld - LISP dyn-eid, a - Application
OE2 ::/0 [110/1], tag 1
     via FE80::15, Ethernet0/2
     via FE80::14, Ethernet0/3
OI  2001:ABCD:EEBB:AAAA:1::/80 [110/20]
     via FE80::14, Ethernet0/3
O   2001:ABCD:EEBB:AAAA:2::/80 [110/20]
     via FE80::14, Ethernet0/3
O   2001:ABCD:EEBB:AAAA:4::/80 [110/20]
     via FE80::15, Ethernet0/2
OI  2001:ABCD:EEBB:AAAA:6::/80 [110/20]
     via FE80::15, Ethernet0/2
OI  2001:ABCD:EEBB:AAAA:19::19/128 [110/20]
     via FE80::14, Ethernet0/3
OI  2001:ABCD:EEBB:AAAA:2222::/80 [110/30]
     via FE80::14, Ethernet0/3
     via FE80::15, Ethernet0/2
OI  2001:ABCD:EEBB:AAAA:3333::/80 [110/30]
     via FE80::14, Ethernet0/3
     via FE80::15, Ethernet0/2
```
### Видем что оба маршрутизатора получают все маршруты и маршрут по умолчанию

**3. Маршрутизатор R19 находится в зоне 101 и получает только маршрут по умолчанию**
```
interface Loopback19
 ip address 77.37.144.19 255.255.255.255
 ipv6 address FE80:1::19 link-local
 ipv6 address 2001:ABCD:EEBB:AAAA:19::19/80
 ipv6 enable
 ipv6 ospf 1 area 101
!
interface Ethernet0/0
 description to --> R14
 ip address 10.10.1.2 255.255.255.252
 ipv6 address FE80::19 link-local
 ipv6 address 2001:ABCD:EEBB:AAAA:1::2/80
 ipv6 enable
 ipv6 ospf 1 area 101
!
router ospf 1
 router-id 19.19.19.19
 area 101 stub
 network 10.10.1.0 0.0.0.3 area 101
 network 77.37.144.19 0.0.0.0 area 101
!
ipv6 router ospf 1
 router-id 19.19.19.19
 area 101 stub
```
#### Проверим таблицу маршрутизации на R19

```
R19#show ip route ospf
Codes: L - local, C - connected, S - static, R - RIP, M - mobile, B - BGP
       D - EIGRP, EX - EIGRP external, O - OSPF, IA - OSPF inter area
       N1 - OSPF NSSA external type 1, N2 - OSPF NSSA external type 2
       E1 - OSPF external type 1, E2 - OSPF external type 2
       i - IS-IS, su - IS-IS summary, L1 - IS-IS level-1, L2 - IS-IS level-2
       ia - IS-IS inter area, * - candidate default, U - per-user static route
       o - ODR, P - periodic downloaded static route, H - NHRP, l - LISP
       a - application route
       + - replicated route, % - next hop override

Gateway of last resort is 10.10.1.1 to network 0.0.0.0

O*IA  0.0.0.0/0 [110/11] via 10.10.1.1, 12:20:23, Ethernet0/0
R19#show ipv6 route ospf
IPv6 Routing Table - default - 6 entries
Codes: C - Connected, L - Local, S - Static, U - Per-user Static route
       B - BGP, HA - Home Agent, MR - Mobile Router, R - RIP
       H - NHRP, I1 - ISIS L1, I2 - ISIS L2, IA - ISIS interarea
       IS - ISIS summary, D - EIGRP, EX - EIGRP external, NM - NEMO
       ND - ND Default, NDp - ND Prefix, DCE - Destination, NDr - Redirect
       O - OSPF Intra, OI - OSPF Inter, OE1 - OSPF ext 1, OE2 - OSPF ext 2
       ON1 - OSPF NSSA ext 1, ON2 - OSPF NSSA ext 2, la - LISP alt
       lr - LISP site-registrations, ld - LISP dyn-eid, a - Application
OI  ::/0 [110/11]
     via FE80::14, Ethernet0/0
```
### Видем что маршрутизатор получает только маршрут по умолчанию

**4. Маршрутизатор R20 находится в зоне 102 и получает все маршруты, кроме маршрутов до сетей зоны 101**

```
interface Loopback20
 ip address 77.37.144.20 255.255.255.255
 ipv6 address FE80:1::20 link-local
 ipv6 enable
 ipv6 ospf 1 area 102
!
interface Ethernet0/0
 description to --> R15
 ip address 10.10.1.22 255.255.255.252
 ipv6 address FE80::20 link-local
 ipv6 address 2001:ABCD:EEBB:AAAA:6::2/80
 ipv6 ospf 1 area 102
!
router ospf 1
 router-id 20.20.20.20
 network 10.10.1.20 0.0.0.3 area 102
 network 77.37.144.20 0.0.0.0 area 102
!
ipv6 router ospf 1
 router-id 20.20.20.20
```
#### Проверим таблицу маршрутизации на R20

```
R20#show ip route ospf
Codes: L - local, C - connected, S - static, R - RIP, M - mobile, B - BGP
       D - EIGRP, EX - EIGRP external, O - OSPF, IA - OSPF inter area
       N1 - OSPF NSSA external type 1, N2 - OSPF NSSA external type 2
       E1 - OSPF external type 1, E2 - OSPF external type 2
       i - IS-IS, su - IS-IS summary, L1 - IS-IS level-1, L2 - IS-IS level-2
       ia - IS-IS inter area, * - candidate default, U - per-user static route
       o - ODR, P - periodic downloaded static route, H - NHRP, l - LISP
       a - application route
       + - replicated route, % - next hop override

Gateway of last resort is 10.10.1.21 to network 0.0.0.0

O*E2  0.0.0.0/0 [110/1] via 10.10.1.21, 12:25:19, Ethernet0/0
      10.0.0.0/8 is variably subnetted, 6 subnets, 2 masks
O IA     10.10.1.4/30 [110/30] via 10.10.1.21, 12:25:19, Ethernet0/0
O IA     10.10.1.8/30 [110/30] via 10.10.1.21, 12:25:19, Ethernet0/0
O IA     10.10.1.12/30 [110/20] via 10.10.1.21, 12:25:19, Ethernet0/0
O IA     10.10.1.16/30 [110/20] via 10.10.1.21, 12:25:19, Ethernet0/0
      77.0.0.0/32 is subnetted, 5 subnets
O IA     77.37.144.12 [110/21] via 10.10.1.21, 12:25:19, Ethernet0/0
O IA     77.37.144.14 [110/31] via 10.10.1.21, 12:25:09, Ethernet0/0
O IA     77.37.144.15 [110/11] via 10.10.1.21, 12:25:19, Ethernet0/0
O IA     77.37.144.19 [110/41] via 10.10.1.21, 11:17:31, Ethernet0/0
      172.16.0.0/16 is variably subnetted, 3 subnets, 2 masks
O IA     172.16.3.0/28 [110/30] via 10.10.1.21, 12:25:19, Ethernet0/0
O IA     172.16.3.16/28 [110/30] via 10.10.1.21, 12:25:19, Ethernet0/0
O IA     172.16.30.0/29 [110/30] via 10.10.1.21, 12:25:19, Ethernet0/0
R20#show ipv6 route ospf
IPv6 Routing Table - default - 12 entries
Codes: C - Connected, L - Local, S - Static, U - Per-user Static route
       B - BGP, HA - Home Agent, MR - Mobile Router, R - RIP
       H - NHRP, I1 - ISIS L1, I2 - ISIS L2, IA - ISIS interarea
       IS - ISIS summary, D - EIGRP, EX - EIGRP external, NM - NEMO
       ND - ND Default, NDp - ND Prefix, DCE - Destination, NDr - Redirect
       O - OSPF Intra, OI - OSPF Inter, OE1 - OSPF ext 1, OE2 - OSPF ext 2
       ON1 - OSPF NSSA ext 1, ON2 - OSPF NSSA ext 2, la - LISP alt
       lr - LISP site-registrations, ld - LISP dyn-eid, a - Application
OE2 ::/0 [110/1], tag 1
     via FE80::15, Ethernet0/0
OI  2001:ABCD:EEBB:AAAA:2::/80 [110/30]
     via FE80::15, Ethernet0/0
OI  2001:ABCD:EEBB:AAAA:3::/80 [110/30]
     via FE80::15, Ethernet0/0
OI  2001:ABCD:EEBB:AAAA:4::/80 [110/20]
     via FE80::15, Ethernet0/0
OI  2001:ABCD:EEBB:AAAA:5::/80 [110/20]
     via FE80::15, Ethernet0/0
OI  2001:ABCD:EEBB:AAAA:19::19/128 [110/40]
     via FE80::15, Ethernet0/0
OI  2001:ABCD:EEBB:AAAA:1111::/80 [110/30]
     via FE80::15, Ethernet0/0
OI  2001:ABCD:EEBB:AAAA:2222::/80 [110/30]
     via FE80::15, Ethernet0/0
OI  2001:ABCD:EEBB:AAAA:3333::/80 [110/30]
     via FE80::15, Ethernet0/0
```

### Видем что маршрутизатор получает все маршруты кроме маршрута до AREA 101
