# Задание
**Настроите IS-IS в ISP Триада**

1. R23 и R25 находятся в зоне 2222.

2. R24 находится в зоне 24.

3. R26 находится в зоне 26.

**Настройка осуществляется одновременно для IPv4 и IPv6**

## Карта сети

>![isis](https://user-images.githubusercontent.com/112701413/202470046-50958105-51c5-4e64-b75e-a7c0d1b453d4.jpg)


### **1. R23 и R25 находятся в зоне 2222**

**R23**
```
interface Loopback23
 ip address 109.72.255.23 255.255.255.255
 ip router isis area2222
 ipv6 address FE80:1::23 link-local
 ipv6 enable
 ipv6 router isis area2222
!
interface Ethernet0/0
 description to --> R22
 ip address 109.72.1.17 255.255.255.252
 ipv6 address FE80::23 link-local
 ipv6 address 2002:ABCD:EEBB:FFFF:8::1/80
 ipv6 enable
!
interface Ethernet0/1
 description to --> R25
 ip address 109.72.1.1 255.255.255.252
 ip router isis area2222
 ipv6 address FE80::23 link-local
 ipv6 address 2002:ABCD:EEBB:FFFF:1::1/80
 ipv6 enable
 ipv6 router isis area2222
!
interface Ethernet0/2
 description to --> R24
 ip address 109.72.1.14 255.255.255.252
 ip router isis area2222
 ipv6 address FE80::23 link-local
 ipv6 address 2002:ABCD:EEBB:FFFF:7::2/80
 ipv6 enable
 ipv6 router isis area2222
!
router isis area2222
 net 49.2222.0023.0023.0023.00
 ```
 
 **R25**
 ```
 interface Loopback25
 ip address 109.72.255.25 255.255.255.255
 ip router isis area2222
 ipv6 address FE80:1::25 link-local
 ipv6 enable
 ipv6 router isis area2222
!
interface Ethernet0/0
 description to --> R23
 ip address 109.72.1.2 255.255.255.252
 ip router isis area2222
 ipv6 address FE80::25 link-local
 ipv6 address 2002:ABCD:EEBB:FFFF:1::2/80
 ipv6 enable
 ipv6 router isis area2222
!
interface Ethernet0/1
 description to --> R27
 ip address 109.72.1.25 255.255.255.252
 ipv6 address FE80::25 link-local
 ipv6 address 2002:ABCD:EEBB:FFFF:3::1/80
 ipv6 enable
!
interface Ethernet0/2
 description to --> R26
 ip address 109.72.1.5 255.255.255.252
 ip router isis area2222
 ipv6 address FE80::25 link-local
 ipv6 address 2002:ABCD:EEBB:FFFF:5::2/80
 ipv6 enable
 ipv6 router isis area2222
!
interface Ethernet0/3
 description to --> R28
 ip address 109.72.1.29 255.255.255.252
 ipv6 address FE80::25 link-local
 ipv6 address 2002:ABCD:EEBB:FFFF:2::1/80
 ipv6 enable
!
router isis area2222
 net 49.2222.0025.0025.0025.00
```
### **2. R24 находится в зоне 24**

**R24**

```
interface Loopback24
 ip address 109.72.255.24 255.255.255.255
 ip router isis area24
 ipv6 address FE80:1::24 link-local
 ipv6 enable
 ipv6 router isis area24
!
interface Ethernet0/0
 description to --> R21
 ip address 109.72.1.21 255.255.255.252
 ipv6 address FE80::24 link-local
 ipv6 address 2002:ABCD:EEBB:FFFF:9::2/80
 ipv6 enable
!
interface Ethernet0/1
 description to --> R26
 ip address 109.72.1.10 255.255.255.252
 ip router isis area24
 ipv6 address FE80::24 link-local
 ipv6 address 2002:ABCD:EEBB:FFFF:6::2/80
 ipv6 enable
 ipv6 router isis area24
!
interface Ethernet0/2
 description to --> R23
 ip address 109.72.1.13 255.255.255.252
 ip router isis area24
 ipv6 address FE80::24 link-local
 ipv6 address 2002:ABCD:EEBB:FFFF:7::1/80
 ipv6 enable
 ipv6 router isis area24
!
interface Ethernet0/3
 description to --> R18
 ip address 109.72.1.37 255.255.255.252
 ipv6 address FE80::24 link-local
 ipv6 address 2002:ABCD:EEBB:FFFF:A::1/80
 ipv6 enable
!
router isis area24
 net 49.0024.0024.0024.0024.00
```

### **3. R26 находится в зоне 26**

**R26**

```
interface Loopback26
 ip address 109.72.255.26 255.255.255.255
 ip router isis area26
 ipv6 address FE80:1::26 link-local
 ipv6 router isis area26
!
interface Ethernet0/0
 description to --> R24
 ip address 109.72.1.9 255.255.255.252
 ip router isis area26
 ipv6 address FE80::26 link-local
 ipv6 address 2002:ABCD:EEBB:FFFF:6::1/80
 ipv6 router isis area26
!
interface Ethernet0/1
 description to --> R28
 ip address 109.72.1.33 255.255.255.252
 ipv6 address FE80::26 link-local
 ipv6 address 2002:ABCD:EEBB:FFFF:4::1/80
!
interface Ethernet0/2
 description to --> R25
 ip address 109.72.1.6 255.255.255.252
 ip router isis area26
 ipv6 address FE80::26 link-local
 ipv6 address 2002:ABCD:EEBB:FFFF:5::1/80
 ipv6 router isis area26
!
interface Ethernet0/3
 description to --> R18
 ip address 109.72.1.41 255.255.255.252
 ipv6 address FE80::26 link-local
 ipv6 address 2002:ABCD:EEBB:FFFF:B::1/80
!
router isis area26
 net 49.0026.0026.0026.0026.00
```

### Проверка 

**23**
```
R23#sh ip route isis 
Codes: L - local, C - connected, S - static, R - RIP, M - mobile, B - BGP
       D - EIGRP, EX - EIGRP external, O - OSPF, IA - OSPF inter area 
       N1 - OSPF NSSA external type 1, N2 - OSPF NSSA external type 2
       E1 - OSPF external type 1, E2 - OSPF external type 2
       i - IS-IS, su - IS-IS summary, L1 - IS-IS level-1, L2 - IS-IS level-2
       ia - IS-IS inter area, * - candidate default, U - per-user static route
       o - ODR, P - periodic downloaded static route, H - NHRP, l - LISP
       a - application route
       + - replicated route, % - next hop override

Gateway of last resort is not set

      109.0.0.0/8 is variably subnetted, 12 subnets, 2 masks
i L1     109.72.1.4/30 [115/20] via 109.72.1.2, 00:34:10, Ethernet0/1
i L2     109.72.1.8/30 [115/20] via 109.72.1.13, 00:33:16, Ethernet0/2
i L2     109.72.255.24/32 [115/20] via 109.72.1.13, 00:33:16, Ethernet0/2
i L1     109.72.255.25/32 [115/20] via 109.72.1.2, 00:34:10, Ethernet0/1
i L2     109.72.255.26/32 [115/30] via 109.72.1.13, 00:33:44, Ethernet0/2
                          [115/30] via 109.72.1.2, 00:33:44, Ethernet0/1
R23#sh ipv6 route isis
IPv6 Routing Table - default - 9 entries
Codes: C - Connected, L - Local, S - Static, U - Per-user Static route
       B - BGP, HA - Home Agent, MR - Mobile Router, R - RIP
       H - NHRP, I1 - ISIS L1, I2 - ISIS L2, IA - ISIS interarea
       IS - ISIS summary, D - EIGRP, EX - EIGRP external, NM - NEMO
       ND - ND Default, NDp - ND Prefix, DCE - Destination, NDr - Redirect
       O - OSPF Intra, OI - OSPF Inter, OE1 - OSPF ext 1, OE2 - OSPF ext 2
       ON1 - OSPF NSSA ext 1, ON2 - OSPF NSSA ext 2, la - LISP alt
       lr - LISP site-registrations, ld - LISP dyn-eid, a - Application
I1  2002:ABCD:EEBB:FFFF:5::/80 [115/20]
     via FE80::25, Ethernet0/1
I2  2002:ABCD:EEBB:FFFF:6::/80 [115/20]
     via FE80::24, Ethernet0/2
```

**R25**

```
R25#show ip route isis
Codes: L - local, C - connected, S - static, R - RIP, M - mobile, B - BGP
       D - EIGRP, EX - EIGRP external, O - OSPF, IA - OSPF inter area 
       N1 - OSPF NSSA external type 1, N2 - OSPF NSSA external type 2
       E1 - OSPF external type 1, E2 - OSPF external type 2
       i - IS-IS, su - IS-IS summary, L1 - IS-IS level-1, L2 - IS-IS level-2
       ia - IS-IS inter area, * - candidate default, U - per-user static route
       o - ODR, P - periodic downloaded static route, H - NHRP, l - LISP
       a - application route
       + - replicated route, % - next hop override

Gateway of last resort is not set

      109.0.0.0/8 is variably subnetted, 14 subnets, 2 masks
i L2     109.72.1.8/30 [115/20] via 109.72.1.6, 00:35:20, Ethernet0/2
i L1     109.72.1.12/30 [115/20] via 109.72.1.1, 00:33:40, Ethernet0/0
i L1     109.72.255.23/32 [115/20] via 109.72.1.1, 00:33:40, Ethernet0/0
i L2     109.72.255.24/32 [115/30] via 109.72.1.6, 00:34:52, Ethernet0/2
                          [115/30] via 109.72.1.1, 00:34:52, Ethernet0/0
i L2     109.72.255.26/32 [115/20] via 109.72.1.6, 00:35:20, Ethernet0/2
R25#show ipv6 route isis
IPv6 Routing Table - default - 11 entries
Codes: C - Connected, L - Local, S - Static, U - Per-user Static route
       B - BGP, HA - Home Agent, MR - Mobile Router, R - RIP
       H - NHRP, I1 - ISIS L1, I2 - ISIS L2, IA - ISIS interarea
       IS - ISIS summary, D - EIGRP, EX - EIGRP external, NM - NEMO
       ND - ND Default, NDp - ND Prefix, DCE - Destination, NDr - Redirect
       O - OSPF Intra, OI - OSPF Inter, OE1 - OSPF ext 1, OE2 - OSPF ext 2
       ON1 - OSPF NSSA ext 1, ON2 - OSPF NSSA ext 2, la - LISP alt
       lr - LISP site-registrations, ld - LISP dyn-eid, a - Application
I2  2002:ABCD:EEBB:FFFF:6::/80 [115/20]
     via FE80::26, Ethernet0/2
I1  2002:ABCD:EEBB:FFFF:7::/80 [115/20]
     via FE80::23, Ethernet0/0
```

**R24**

```
R24#show ip route isis
Codes: L - local, C - connected, S - static, R - RIP, M - mobile, B - BGP
       D - EIGRP, EX - EIGRP external, O - OSPF, IA - OSPF inter area 
       N1 - OSPF NSSA external type 1, N2 - OSPF NSSA external type 2
       E1 - OSPF external type 1, E2 - OSPF external type 2
       i - IS-IS, su - IS-IS summary, L1 - IS-IS level-1, L2 - IS-IS level-2
       ia - IS-IS inter area, * - candidate default, U - per-user static route
       o - ODR, P - periodic downloaded static route, H - NHRP, l - LISP
       a - application route
       + - replicated route, % - next hop override

Gateway of last resort is not set

      109.0.0.0/8 is variably subnetted, 14 subnets, 2 masks
i L2     109.72.1.0/30 [115/20] via 109.72.1.14, 00:34:57, Ethernet0/2
i L2     109.72.1.4/30 [115/20] via 109.72.1.9, 00:36:37, Ethernet0/1
i L2     109.72.255.23/32 [115/20] via 109.72.1.14, 00:34:57, Ethernet0/2
i L2     109.72.255.25/32 [115/30] via 109.72.1.14, 00:34:57, Ethernet0/2
                          [115/30] via 109.72.1.9, 00:34:57, Ethernet0/1
i L2     109.72.255.26/32 [115/20] via 109.72.1.9, 00:36:37, Ethernet0/1
R24#show ipv6 route isis
IPv6 Routing Table - default - 11 entries
Codes: C - Connected, L - Local, S - Static, U - Per-user Static route
       B - BGP, HA - Home Agent, MR - Mobile Router, R - RIP
       H - NHRP, I1 - ISIS L1, I2 - ISIS L2, IA - ISIS interarea
       IS - ISIS summary, D - EIGRP, EX - EIGRP external, NM - NEMO
       ND - ND Default, NDp - ND Prefix, DCE - Destination, NDr - Redirect
       O - OSPF Intra, OI - OSPF Inter, OE1 - OSPF ext 1, OE2 - OSPF ext 2
       ON1 - OSPF NSSA ext 1, ON2 - OSPF NSSA ext 2, la - LISP alt
       lr - LISP site-registrations, ld - LISP dyn-eid, a - Application
I2  2002:ABCD:EEBB:FFFF:1::/80 [115/20]
     via FE80::23, Ethernet0/2
I2  2002:ABCD:EEBB:FFFF:5::/80 [115/20]
     via FE80::26, Ethernet0/1
```

**R26**

```
R26#show ip route isis
Codes: L - local, C - connected, S - static, R - RIP, M - mobile, B - BGP
       D - EIGRP, EX - EIGRP external, O - OSPF, IA - OSPF inter area 
       N1 - OSPF NSSA external type 1, N2 - OSPF NSSA external type 2
       E1 - OSPF external type 1, E2 - OSPF external type 2
       i - IS-IS, su - IS-IS summary, L1 - IS-IS level-1, L2 - IS-IS level-2
       ia - IS-IS inter area, * - candidate default, U - per-user static route
       o - ODR, P - periodic downloaded static route, H - NHRP, l - LISP
       a - application route
       + - replicated route, % - next hop override

Gateway of last resort is not set

      109.0.0.0/8 is variably subnetted, 14 subnets, 2 masks
i L2     109.72.1.0/30 [115/20] via 109.72.1.5, 00:38:03, Ethernet0/2
i L2     109.72.1.12/30 [115/20] via 109.72.1.10, 00:37:09, Ethernet0/0
i L2     109.72.255.23/32 [115/30] via 109.72.1.10, 00:35:52, Ethernet0/0
                          [115/30] via 109.72.1.5, 00:35:52, Ethernet0/2
i L2     109.72.255.24/32 [115/20] via 109.72.1.10, 00:37:09, Ethernet0/0
i L2     109.72.255.25/32 [115/20] via 109.72.1.5, 00:38:03, Ethernet0/2
R26#show ipv6 route isis
IPv6 Routing Table - default - 11 entries
Codes: C - Connected, L - Local, S - Static, U - Per-user Static route
       B - BGP, HA - Home Agent, MR - Mobile Router, R - RIP
       H - NHRP, I1 - ISIS L1, I2 - ISIS L2, IA - ISIS interarea
       IS - ISIS summary, D - EIGRP, EX - EIGRP external, NM - NEMO
       ND - ND Default, NDp - ND Prefix, DCE - Destination, NDr - Redirect
       O - OSPF Intra, OI - OSPF Inter, OE1 - OSPF ext 1, OE2 - OSPF ext 2
       ON1 - OSPF NSSA ext 1, ON2 - OSPF NSSA ext 2, la - LISP alt
       lr - LISP site-registrations, ld - LISP dyn-eid, a - Application
I2  2002:ABCD:EEBB:FFFF:1::/80 [115/20]
     via FE80::25, Ethernet0/2
I2  2002:ABCD:EEBB:FFFF:7::/80 [115/20]
     via FE80::24, Ethernet0/0
```

#### Видим что все роутеры обмениваются друг с другом маршрутами 
