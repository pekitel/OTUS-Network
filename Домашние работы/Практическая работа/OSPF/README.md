# Задание

## Настроить OSPF офисе Москва Разделить сеть на зоны Настроить фильтрацию между зонами

**1. Маршрутизаторы R14-R15 находятся в зоне 0 - backbone**

**2. Маршрутизаторы R12-R13 находятся в зоне 10. Дополнительно к маршрутам должны получать маршрут по-умолчанию**

**3. Маршрутизатор R19 находится в зоне 101 и получает только маршрут по умолчанию**

**4. Маршрутизатор R20 находится в зоне 102 и получает все маршруты, кроме маршрутов до сетей зоны 101**

**5. План работы и изменения зафиксированы в документации**

### Схема сети

>![ospf](https://user-images.githubusercontent.com/112701413/202281749-3484c9fa-b71e-4a7a-a9ff-d4020f274b7a.jpg)


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
