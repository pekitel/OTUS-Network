# Задание
### Настроить EIGRP в С.-Петербург; Использовать named EIGRP для IPv4 и IPv6


## Схема сети

>![EIGRP](https://user-images.githubusercontent.com/112701413/202871892-f8d4b885-0633-4994-a664-8f45a4dbf982.jpg)

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
router eigrp DUAL-STACK
 !
 address-family ipv4 unicast autonomous-system 1
  !
  af-interface Ethernet0/1
   summary-address 172.16.1.0 255.255.255.224
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
  topology base
  exit-af-topology
  eigrp router-id 17.17.17.17
 exit-address-family
 ```
 
 **Посмотрим список маршрутов IPv4**
 
 ```
 
