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
ip forward-protocol nd
!
!
no ip http server
no ip http secure-server
ip route 0.0.0.0 0.0.0.0 82.138.2.1
!
ipv6 route ::/0 2000:ABCD:EEBB:FFFF:1::1
ipv6 router ospf 1
 router-id 14.14.14.14
 default-information originate
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
ip forward-protocol nd
!
!
no ip http server
no ip http secure-server
ip route 0.0.0.0 0.0.0.0 77.94.165.1
!
!
ip prefix-list PL1 seq 5 deny 10.10.1.0/30
ip prefix-list PL1 seq 10 permit 0.0.0.0/0 le 32
ipv6 route ::/0 1999:ABCD:EEBB:FFFF:1::1
ipv6 router ospf 1
 router-id 15.15.15.15
 distribute-list prefix-list PL2 in
 default-information originate
!
!
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
