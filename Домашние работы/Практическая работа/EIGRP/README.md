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

## R17
