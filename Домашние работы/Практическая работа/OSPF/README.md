# Задание

## Настроить OSPF офисе Москва Разделить сеть на зоны Настроить фильтрацию между зонами

**1. Маршрутизаторы R14-R15 находятся в зоне 0 - backbone**

**2. Маршрутизаторы R12-R13 находятся в зоне 10. Дополнительно к маршрутам должны получать маршрут по-умолчанию**

**3. Маршрутизатор R19 находится в зоне 101 и получает только маршрут по умолчанию**

**4. Маршрутизатор R20 находится в зоне 102 и получает все маршруты, кроме маршрутов до сетей зоны 101**

**5. План работы и изменения зафиксированы в документации**

### Схема сети

>![ospf](https://user-images.githubusercontent.com/112701413/202281749-3484c9fa-b71e-4a7a-a9ff-d4020f274b7a.jpg)


Маршрутизаторы R14-R15 находятся в зоне 0 - backbone

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
