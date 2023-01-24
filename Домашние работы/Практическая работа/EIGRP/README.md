# Задание
### В офисе С.-Петербург настроить EIGRP.
### R32 получает только маршрут по умолчанию.
### R16-17 анонсируют только суммарные префиксы.
### Настроить EIGRP в С.-Петербург; Использовать named *EIGRP* для *IPv4* и *IPv6*

[R18](https://github.com/pekitel/OTUS-Network/blob/main/%D0%94%D0%BE%D0%BC%D0%B0%D1%88%D0%BD%D0%B8%D0%B5%20%D1%80%D0%B0%D0%B1%D0%BE%D1%82%D1%8B/%D0%9F%D1%80%D0%B0%D0%BA%D1%82%D0%B8%D1%87%D0%B5%D1%81%D0%BA%D0%B0%D1%8F%20%D1%80%D0%B0%D0%B1%D0%BE%D1%82%D0%B0/EIGRP/README.md#r18)

[R17](https://github.com/pekitel/OTUS-Network/blob/main/%D0%94%D0%BE%D0%BC%D0%B0%D1%88%D0%BD%D0%B8%D0%B5%20%D1%80%D0%B0%D0%B1%D0%BE%D1%82%D1%8B/%D0%9F%D1%80%D0%B0%D0%BA%D1%82%D0%B8%D1%87%D0%B5%D1%81%D0%BA%D0%B0%D1%8F%20%D1%80%D0%B0%D0%B1%D0%BE%D1%82%D0%B0/EIGRP/README.md#r17)

[R16](https://github.com/pekitel/OTUS-Network/blob/main/%D0%94%D0%BE%D0%BC%D0%B0%D1%88%D0%BD%D0%B8%D0%B5%20%D1%80%D0%B0%D0%B1%D0%BE%D1%82%D1%8B/%D0%9F%D1%80%D0%B0%D0%BA%D1%82%D0%B8%D1%87%D0%B5%D1%81%D0%BA%D0%B0%D1%8F%20%D1%80%D0%B0%D0%B1%D0%BE%D1%82%D0%B0/EIGRP/README.md#r16)

[R32](https://github.com/pekitel/OTUS-Network/blob/main/%D0%94%D0%BE%D0%BC%D0%B0%D1%88%D0%BD%D0%B8%D0%B5%20%D1%80%D0%B0%D0%B1%D0%BE%D1%82%D1%8B/%D0%9F%D1%80%D0%B0%D0%BA%D1%82%D0%B8%D1%87%D0%B5%D1%81%D0%BA%D0%B0%D1%8F%20%D1%80%D0%B0%D0%B1%D0%BE%D1%82%D0%B0/EIGRP/README.md#r32)

## Схема сети

>![EIGRP](https://user-images.githubusercontent.com/112701413/202894391-791a2c53-f0b0-4cfb-9026-35af0d7c36bf.jpg)


## R18

```
ip dhcp pool VPC8
 network 172.16.1.0 255.255.255.240
 dns-server 8.8.8.8 
 default-router 172.16.1.1 
!
ip dhcp pool VPC
 network 172.16.1.16 255.255.255.240
 dns-server 8.8.8.8 
 default-router 172.16.1.17 
!         
ip cef
ipv6 unicast-routing
ipv6 cef
ipv6 dhcp pool VPC8
 address prefix 2003:ABCD:EEBB:BBBB:2222::1/80
 dns-server 2A02:6B8::FEED:FF
 domain-name spb1.ru
!
ipv6 dhcp pool VPC
 address prefix 2003:ABCD:EEBB:BBBB:3333::1/80
 dns-server 2A02:6B8::FEED:FF
 domain-name spb2.ru
!
interface Loopback18
 ip address 33.72.66.18 255.255.255.255
 ipv6 address FE80:1::18 link-local
 ipv6 enable
!
interface Ethernet0/0
 description to --> R16
 ip address 10.10.2.5 255.255.255.252
 ipv6 address FE80::18 link-local
 ipv6 address 2003:ABCD:EEBB:BBBB:2::1/80
 ipv6 enable
!
interface Ethernet0/1
 description to --> R17
 ip address 10.10.2.1 255.255.255.252
 ipv6 address FE80::18 link-local
 ipv6 address 2003:ABCD:EEBB:BBBB:1::1/80
 ipv6 enable
!
interface Ethernet0/2
 description to --> R24
 ip address 109.72.1.38 255.255.255.252
 ipv6 address FE80::18 link-local
 ipv6 address 2002:ABCD:EEBB:FFFF:A::2/80
 ipv6 enable
!
interface Ethernet0/3
 description to --> R26
 ip address 109.72.1.42 255.255.255.252
 ipv6 address FE80::18 link-local
 ipv6 address 2002:ABCD:EEBB:FFFF:B::2/80
 ipv6 enable
!
router eigrp DUAL-STACK
 !
 address-family ipv4 unicast autonomous-system 1
  !
  topology base
   redistribute static
  exit-af-topology
  network 10.10.2.0 0.0.0.3
  network 10.10.2.4 0.0.0.3
  network 33.72.66.18 0.0.0.0
 exit-address-family
 !
 address-family ipv6 unicast autonomous-system 2
  !
  topology base
   redistribute static
  exit-af-topology
  eigrp router-id 18.18.18.18
 exit-address-family
!
no ip http server
no ip http secure-server
ip route 0.0.0.0 0.0.0.0 109.72.1.37
ip route 0.0.0.0 0.0.0.0 109.72.1.41
!
ipv6 route ::/0 2002:ABCD:EEBB:FFFF:A::1
ipv6 route ::/0 2002:ABCD:EEBB:FFFF:B::1
```

**Посмотрим список маршрутов IPv4**

```
R18#show ip route eigrp 
Codes: L - local, C - connected, S - static, R - RIP, M - mobile, B - BGP
       D - EIGRP, EX - EIGRP external, O - OSPF, IA - OSPF inter area 
       N1 - OSPF NSSA external type 1, N2 - OSPF NSSA external type 2
       E1 - OSPF external type 1, E2 - OSPF external type 2
       i - IS-IS, su - IS-IS summary, L1 - IS-IS level-1, L2 - IS-IS level-2
       ia - IS-IS inter area, * - candidate default, U - per-user static route
       o - ODR, P - periodic downloaded static route, H - NHRP, l - LISP
       a - application route
       + - replicated route, % - next hop override

Gateway of last resort is 109.72.1.41 to network 0.0.0.0

      10.0.0.0/8 is variably subnetted, 5 subnets, 2 masks
D        10.10.2.8/30 [90/1536000] via 10.10.2.6, 01:47:53, Ethernet0/0
      33.0.0.0/32 is subnetted, 3 subnets
D        33.72.66.16 [90/1024640] via 10.10.2.6, 00:33:17, Ethernet0/0
D        33.72.66.17 [90/1024640] via 10.10.2.2, 00:36:19, Ethernet0/1
      172.16.0.0/16 is variably subnetted, 2 subnets, 2 masks
D        172.16.1.0/27 [90/1536000] via 10.10.2.2, 01:35:14, Ethernet0/1
D        172.16.10.0/29 [90/1536000] via 10.10.2.6, 01:47:53, Ethernet0/0
```

**Посмотрим список маршрутов IPv6**

```
R18#show ipv6 route eigrp 
IPv6 Routing Table - default - 13 entries
Codes: C - Connected, L - Local, S - Static, U - Per-user Static route
       B - BGP, HA - Home Agent, MR - Mobile Router, R - RIP
       H - NHRP, I1 - ISIS L1, I2 - ISIS L2, IA - ISIS interarea
       IS - ISIS summary, D - EIGRP, EX - EIGRP external, NM - NEMO
       ND - ND Default, NDp - ND Prefix, DCE - Destination, NDr - Redirect
       O - OSPF Intra, OI - OSPF Inter, OE1 - OSPF ext 1, OE2 - OSPF ext 2
       ON1 - OSPF NSSA ext 1, ON2 - OSPF NSSA ext 2, la - LISP alt
       lr - LISP site-registrations, ld - LISP dyn-eid, a - Application
D   2003:ABCD:EEBB:BBBB::/64 [90/1536000]
     via FE80::17, Ethernet0/1
D   2003:ABCD:EEBB:BBBB:3::/80 [90/1536000]
     via FE80::16, Ethernet0/0
D   2003:ABCD:EEBB:BBBB:1111::/80 [90/1536000]
     via FE80::16, Ethernet0/0
```

## R17

```
ip cef
ipv6 unicast-routing
ipv6 cef
!
interface Loopback17
 ip address 33.72.66.17 255.255.255.255
 ipv6 address FE80:1::17 link-local
 ipv6 enable
!
interface Ethernet0/0
 no ip address
!
interface Ethernet0/0.10
 description to --> VPC8
 encapsulation dot1Q 10
 ip address 172.16.1.1 255.255.255.240
 ip helper-address 10.10.2.1
 ipv6 address FE80::17 link-local
 ipv6 address 2003:ABCD:EEBB:BBBB:2222::1/80
 ipv6 enable
 ipv6 nd managed-config-flag
 ipv6 dhcp relay destination  2003:ABCD:EEBB:BBBB:1::1
!
interface Ethernet0/0.20
 description to --> VPC
 encapsulation dot1Q 20
 ip address 172.16.1.17 255.255.255.240
 ip helper-address 10.10.2.1
 ipv6 address FE80::17 link-local
 ipv6 address 2003:ABCD:EEBB:BBBB:3333::1/80
 ipv6 enable
 ipv6 nd managed-config-flag
 ipv6 dhcp relay destination  2003:ABCD:EEBB:BBBB:1::1
!
interface Ethernet0/1
 description to --> R18
 ip address 10.10.2.2 255.255.255.252
 ipv6 address FE80::17 link-local
 ipv6 address 2003:ABCD:EEBB:BBBB:1::2/80
 ipv6 enable
!
interface Ethernet0/2
 no ip address
 shutdown
!
interface Ethernet0/3
 no ip address
 shutdown
!
router eigrp DUAL-STACK
 !
 address-family ipv4 unicast autonomous-system 1
  !
  af-interface Ethernet0/1
   summary-address 172.16.1.0 255.255.255.224
  exit-af-interface
  !
  af-interface Ethernet0/2
   passive-interface
  exit-af-interface
  !
  af-interface Ethernet0/3
   passive-interface
  exit-af-interface
  !
  topology base
  exit-af-topology
  network 10.10.2.0 0.0.0.3
  network 33.72.66.17 0.0.0.0
  network 172.16.1.0 0.0.0.31
  eigrp router-id 17.17.17.17
 exit-address-family
 !
 address-family ipv6 unicast autonomous-system 2
  !       
  af-interface Ethernet0/1
   summary-address 2003:ABCD:EEBB:BBBB::/64
  exit-af-interface
  !
  af-interface Ethernet0/2
   passive-interface
  exit-af-interface
  !
  af-interface Ethernet0/3
   passive-interface
  exit-af-interface
  !
  topology base
  exit-af-topology
  eigrp router-id 17.17.17.17
 exit-address-family
```
 
 **Посмотрим список маршрутов IPv4**
 
```
R17#show ip route eigrp 
Codes: L - local, C - connected, S - static, R - RIP, M - mobile, B - BGP
       D - EIGRP, EX - EIGRP external, O - OSPF, IA - OSPF inter area 
       N1 - OSPF NSSA external type 1, N2 - OSPF NSSA external type 2
       E1 - OSPF external type 1, E2 - OSPF external type 2
       i - IS-IS, su - IS-IS summary, L1 - IS-IS level-1, L2 - IS-IS level-2
       ia - IS-IS inter area, * - candidate default, U - per-user static route
       o - ODR, P - periodic downloaded static route, H - NHRP, l - LISP
       a - application route
       + - replicated route, % - next hop override

Gateway of last resort is 10.10.2.1 to network 0.0.0.0

D*EX  0.0.0.0/0 [170/1536000] via 10.10.2.1, 20:10:50, Ethernet0/1
      10.0.0.0/8 is variably subnetted, 4 subnets, 2 masks
D        10.10.2.4/30 [90/1536000] via 10.10.2.1, 20:10:50, Ethernet0/1
D        10.10.2.8/30 [90/2048000] via 10.10.2.1, 20:10:50, Ethernet0/1
      33.0.0.0/32 is subnetted, 3 subnets
D        33.72.66.16 [90/1536640] via 10.10.2.1, 18:59:04, Ethernet0/1
D        33.72.66.18 [90/1024640] via 10.10.2.1, 19:00:49, Ethernet0/1
      172.16.0.0/16 is variably subnetted, 6 subnets, 4 masks
D        172.16.1.0/27 is a summary, 20:01:01, Null0
D        172.16.10.0/29 [90/2048000] via 10.10.2.1, 20:10:50, Ethernet0/1
```
 
 **Посмотрим список маршрутов IPv6**
 
```
R17#show ipv6 route eigrp 
IPv6 Routing Table - default - 13 entries
Codes: C - Connected, L - Local, S - Static, U - Per-user Static route
       B - BGP, HA - Home Agent, MR - Mobile Router, R - RIP
       H - NHRP, I1 - ISIS L1, I2 - ISIS L2, IA - ISIS interarea
       IS - ISIS summary, D - EIGRP, EX - EIGRP external, NM - NEMO
       ND - ND Default, NDp - ND Prefix, DCE - Destination, NDr - Redirect
       O - OSPF Intra, OI - OSPF Inter, OE1 - OSPF ext 1, OE2 - OSPF ext 2
       ON1 - OSPF NSSA ext 1, ON2 - OSPF NSSA ext 2, la - LISP alt
       lr - LISP site-registrations, ld - LISP dyn-eid, a - Application
D   2002:ABCD:EEBB:FFFF:A::/80 [90/1536000]
     via FE80::18, Ethernet0/1
D   2002:ABCD:EEBB:FFFF:B::/80 [90/1536000]
     via FE80::18, Ethernet0/1
D   2003:ABCD:EEBB:BBBB::/64 [5/1024000]
     via Null0, directly connected
D   2003:ABCD:EEBB:BBBB:2::/80 [90/1536000]
     via FE80::18, Ethernet0/1
D   2003:ABCD:EEBB:BBBB:3::/80 [90/2048000]
     via FE80::18, Ethernet0/1
D   2003:ABCD:EEBB:BBBB:1111::/80 [90/2048000]
     via FE80::18, Ethernet0/1
```

## R16

```
ip cef
ipv6 unicast-routing
ipv6 cef
!
interface Loopback16
 ip address 33.72.66.16 255.255.255.255
 ipv6 address FE80:1::16 link-local
 ipv6 enable
!
interface Ethernet0/0
 no ip address
!
interface Ethernet0/0.99
 description MGMT
 encapsulation dot1Q 99
 ip address 172.16.10.1 255.255.255.248
 ipv6 address FE80::16 link-local
 ipv6 address 2003:ABCD:EEBB:BBBB:1111::1/80
 ipv6 enable
!
interface Ethernet0/0.777
 encapsulation dot1Q 777 native
!
interface Ethernet0/1
 description to --> R18
 ip address 10.10.2.6 255.255.255.252
 ipv6 address FE80::16 link-local
 ipv6 address 2003:ABCD:EEBB:BBBB:2::2/80
 ipv6 enable
!         
interface Ethernet0/2
 no ip address
 shutdown
!
interface Ethernet0/3
 description to --> R32
 ip address 10.10.2.9 255.255.255.252
 ipv6 address FE80::16 link-local
 ipv6 address 2003:ABCD:EEBB:BBBB:3::1/80
 ipv6 enable
!
router eigrp DUAL-STACK
 !
 address-family ipv4 unicast autonomous-system 1
  !
  af-interface Ethernet0/3
   summary-address 0.0.0.0 0.0.0.0
  exit-af-interface
  !
  af-interface Ethernet0/1
   no next-hop-self
  exit-af-interface
  !
  af-interface Ethernet0/0.99
   passive-interface
  exit-af-interface
  !
  af-interface Ethernet0/2
   passive-interface
  exit-af-interface
  !
  topology base
  exit-af-topology
  neighbor 10.10.2.10 Ethernet0/3
  network 10.10.2.4 0.0.0.3
  network 10.10.2.8 0.0.0.3
  network 33.72.66.16 0.0.0.0
  network 172.16.10.0 0.0.0.7
  eigrp router-id 16.16.16.16
 exit-address-family
 !
 address-family ipv6 unicast autonomous-system 2
  !
  af-interface Ethernet0/3
   summary-address ::/0
  exit-af-interface
  !
  af-interface Ethernet0/2
   passive-interface
  exit-af-interface
  !
  topology base
  exit-af-topology
 exit-address-family
```
 **Посмотрим список маршрутов IPv4**
 
```
R16#show ip route eigrp 
Codes: L - local, C - connected, S - static, R - RIP, M - mobile, B - BGP
       D - EIGRP, EX - EIGRP external, O - OSPF, IA - OSPF inter area 
       N1 - OSPF NSSA external type 1, N2 - OSPF NSSA external type 2
       E1 - OSPF external type 1, E2 - OSPF external type 2
       i - IS-IS, su - IS-IS summary, L1 - IS-IS level-1, L2 - IS-IS level-2
       ia - IS-IS inter area, * - candidate default, U - per-user static route
       o - ODR, P - periodic downloaded static route, H - NHRP, l - LISP
       a - application route
       + - replicated route, % - next hop override

Gateway of last resort is 0.0.0.0 to network 0.0.0.0

D*    0.0.0.0/0 is a summary, 19:06:05, Null0
      10.0.0.0/8 is variably subnetted, 5 subnets, 2 masks
D        10.10.2.0/30 [90/1536000] via 10.10.2.5, 20:20:35, Ethernet0/1
      33.0.0.0/32 is subnetted, 3 subnets
D        33.72.66.17 [90/1536640] via 10.10.2.5, 19:09:07, Ethernet0/1
D        33.72.66.18 [90/1024640] via 10.10.2.5, 19:07:50, Ethernet0/1
      172.16.0.0/16 is variably subnetted, 3 subnets, 3 masks
D        172.16.1.0/27 [90/2048000] via 10.10.2.5, 20:08:02, Ethernet0/1
```

 **Посмотрим список маршрутов IPv6**
 
```
R16#show ipv6 route eigrp 
IPv6 Routing Table - default - 12 entries
Codes: C - Connected, L - Local, S - Static, U - Per-user Static route
       B - BGP, HA - Home Agent, MR - Mobile Router, R - RIP
       H - NHRP, I1 - ISIS L1, I2 - ISIS L2, IA - ISIS interarea
       IS - ISIS summary, D - EIGRP, EX - EIGRP external, NM - NEMO
       ND - ND Default, NDp - ND Prefix, DCE - Destination, NDr - Redirect
       O - OSPF Intra, OI - OSPF Inter, OE1 - OSPF ext 1, OE2 - OSPF ext 2
       ON1 - OSPF NSSA ext 1, ON2 - OSPF NSSA ext 2, la - LISP alt
       lr - LISP site-registrations, ld - LISP dyn-eid, a - Application
D   ::/0 [5/1024000]
     via Null0, directly connected
D   2002:ABCD:EEBB:FFFF:A::/80 [90/1536000]
     via FE80::18, Ethernet0/1
D   2002:ABCD:EEBB:FFFF:B::/80 [90/1536000]
     via FE80::18, Ethernet0/1
D   2003:ABCD:EEBB:BBBB::/64 [90/2048000]
     via FE80::18, Ethernet0/1
D   2003:ABCD:EEBB:BBBB:1::/80 [90/1536000]
     via FE80::18, Ethernet0/1
```

## R32

```
ip cef
ipv6 unicast-routing
ipv6 cef
!
interface Loopback32
 ip address 33.72.66.32 255.255.255.255
 ipv6 address FE80:1::32 link-local
 ipv6 enable
!
interface Ethernet0/0
 description to --> R16
 ip address 10.10.2.10 255.255.255.252
 ipv6 address FE80::32 link-local
 ipv6 address 2003:ABCD:EEBB:BBBB:3::2/80
 ipv6 enable
!
interface Ethernet0/1
 no ip address
 shutdown
!
interface Ethernet0/2
 no ip address
 shutdown
!
interface Ethernet0/3
 no ip address
 shutdown
!
router eigrp DUAL-STACK
 !
 address-family ipv4 unicast autonomous-system 1
  !
  af-interface Ethernet0/1
   passive-interface
  exit-af-interface
  !
  af-interface Ethernet0/2
   passive-interface
  exit-af-interface
  !
  af-interface Ethernet0/3
   passive-interface
  exit-af-interface
  !
  topology base
  exit-af-topology
  neighbor 10.10.2.9 Ethernet0/0
  network 10.10.2.8 0.0.0.3
  eigrp router-id 32.32.32.32
 exit-address-family
 !
 address-family ipv6 unicast autonomous-system 2
  !
  af-interface Ethernet0/1
   passive-interface
  exit-af-interface
  !
  af-interface Ethernet0/2
   passive-interface
  exit-af-interface
  !
  af-interface Ethernet0/3
   passive-interface
  exit-af-interface
  !
  topology base
  exit-af-topology
  eigrp router-id 32.32.32.32
 exit-address-family
```
**Посмотрим список маршрутов IPv4**
```
R32#show ip route eigrp 
Codes: L - local, C - connected, S - static, R - RIP, M - mobile, B - BGP
       D - EIGRP, EX - EIGRP external, O - OSPF, IA - OSPF inter area 
       N1 - OSPF NSSA external type 1, N2 - OSPF NSSA external type 2
       E1 - OSPF external type 1, E2 - OSPF external type 2
       i - IS-IS, su - IS-IS summary, L1 - IS-IS level-1, L2 - IS-IS level-2
       ia - IS-IS inter area, * - candidate default, U - per-user static route
       o - ODR, P - periodic downloaded static route, H - NHRP, l - LISP
       a - application route
       + - replicated route, % - next hop override

Gateway of last resort is 10.10.2.9 to network 0.0.0.0

D*    0.0.0.0/0 [90/1024640] via 10.10.2.9, 19:12:17, Ethernet0/0
```
**Посмотрим список маршрутов IPv6**
```
R32#show ipv6 route eigrp 
IPv6 Routing Table - default - 4 entries
Codes: C - Connected, L - Local, S - Static, U - Per-user Static route
       B - BGP, HA - Home Agent, MR - Mobile Router, R - RIP
       H - NHRP, I1 - ISIS L1, I2 - ISIS L2, IA - ISIS interarea
       IS - ISIS summary, D - EIGRP, EX - EIGRP external, NM - NEMO
       ND - ND Default, NDp - ND Prefix, DCE - Destination, NDr - Redirect
       O - OSPF Intra, OI - OSPF Inter, OE1 - OSPF ext 1, OE2 - OSPF ext 2
       ON1 - OSPF NSSA ext 1, ON2 - OSPF NSSA ext 2, la - LISP alt
       lr - LISP site-registrations, ld - LISP dyn-eid, a - Application
D   ::/0 [90/1536000]
     via FE80::16, Ethernet0/0
```
