# Задание

## Настроить DHCP в офисе Москва
## Настроить синхронизацию времени в офисе Москва
## Настроить NAT в офисе Москва, C.-Перетбруг и Чокурдах

1. [Настроите NAT(PAT) на R14 и R15. Трансляция должна осуществляться в адрес автономной системы AS1001.](https://github.com/pekitel/OTUS-Network/blob/main/%D0%94%D0%BE%D0%BC%D0%B0%D1%88%D0%BD%D0%B8%D0%B5%20%D1%80%D0%B0%D0%B1%D0%BE%D1%82%D1%8B/%D0%9F%D1%80%D0%B0%D0%BA%D1%82%D0%B8%D1%87%D0%B5%D1%81%D0%BA%D0%B0%D1%8F%20%D1%80%D0%B0%D0%B1%D0%BE%D1%82%D0%B0/%D0%9E%D1%81%D0%BD%D0%BE%D0%B2%D0%BD%D1%8B%D0%B5%20%D0%BF%D1%80%D0%BE%D1%82%D0%BE%D0%BA%D0%BE%D0%BB%D1%8B%20%D1%81%D0%B5%D1%82%D0%B8%20%D0%B8%D0%BD%D1%82%D0%B5%D1%80%D0%BD%D0%B5%D1%82/README.md#%D0%BD%D0%B0%D1%81%D1%82%D1%80%D0%BE%D0%B8%D1%82%D0%B5-natpat-%D0%BD%D0%B0-r14-%D0%B8-r15-%D1%82%D1%80%D0%B0%D0%BD%D1%81%D0%BB%D1%8F%D1%86%D0%B8%D1%8F-%D0%B4%D0%BE%D0%BB%D0%B6%D0%BD%D0%B0-%D0%BE%D1%81%D1%83%D1%89%D0%B5%D1%81%D1%82%D0%B2%D0%BB%D1%8F%D1%82%D1%8C%D1%81%D1%8F-%D0%B2-%D0%B0%D0%B4%D1%80%D0%B5%D1%81-%D0%B0%D0%B2%D1%82%D0%BE%D0%BD%D0%BE%D0%BC%D0%BD%D0%BE%D0%B9-%D1%81%D0%B8%D1%81%D1%82%D0%B5%D0%BC%D1%8B-as1001)
2. [Настроите NAT(PAT) на R18. Трансляция должна осуществляться в пул из 5 адресов автономной системы AS2042.](https://github.com/pekitel/OTUS-Network/blob/main/%D0%94%D0%BE%D0%BC%D0%B0%D1%88%D0%BD%D0%B8%D0%B5%20%D1%80%D0%B0%D0%B1%D0%BE%D1%82%D1%8B/%D0%9F%D1%80%D0%B0%D0%BA%D1%82%D0%B8%D1%87%D0%B5%D1%81%D0%BA%D0%B0%D1%8F%20%D1%80%D0%B0%D0%B1%D0%BE%D1%82%D0%B0/%D0%9E%D1%81%D0%BD%D0%BE%D0%B2%D0%BD%D1%8B%D0%B5%20%D0%BF%D1%80%D0%BE%D1%82%D0%BE%D0%BA%D0%BE%D0%BB%D1%8B%20%D1%81%D0%B5%D1%82%D0%B8%20%D0%B8%D0%BD%D1%82%D0%B5%D1%80%D0%BD%D0%B5%D1%82/README.md#%D0%BD%D0%B0%D1%81%D1%82%D1%80%D0%BE%D0%B8%D1%82%D0%B5-natpat-%D0%BD%D0%B0-r18-%D1%82%D1%80%D0%B0%D0%BD%D1%81%D0%BB%D1%8F%D1%86%D0%B8%D1%8F-%D0%B4%D0%BE%D0%BB%D0%B6%D0%BD%D0%B0-%D0%BE%D1%81%D1%83%D1%89%D0%B5%D1%81%D1%82%D0%B2%D0%BB%D1%8F%D1%82%D1%8C%D1%81%D1%8F-%D0%B2-%D0%BF%D1%83%D0%BB-%D0%B8%D0%B7-5-%D0%B0%D0%B4%D1%80%D0%B5%D1%81%D0%BE%D0%B2-%D0%B0%D0%B2%D1%82%D0%BE%D0%BD%D0%BE%D0%BC%D0%BD%D0%BE%D0%B9-%D1%81%D0%B8%D1%81%D1%82%D0%B5%D0%BC%D1%8B-as2042)
3. [Настроите статический NAT для R20.](https://github.com/pekitel/OTUS-Network/blob/main/%D0%94%D0%BE%D0%BC%D0%B0%D1%88%D0%BD%D0%B8%D0%B5%20%D1%80%D0%B0%D0%B1%D0%BE%D1%82%D1%8B/%D0%9F%D1%80%D0%B0%D0%BA%D1%82%D0%B8%D1%87%D0%B5%D1%81%D0%BA%D0%B0%D1%8F%20%D1%80%D0%B0%D0%B1%D0%BE%D1%82%D0%B0/%D0%9E%D1%81%D0%BD%D0%BE%D0%B2%D0%BD%D1%8B%D0%B5%20%D0%BF%D1%80%D0%BE%D1%82%D0%BE%D0%BA%D0%BE%D0%BB%D1%8B%20%D1%81%D0%B5%D1%82%D0%B8%20%D0%B8%D0%BD%D1%82%D0%B5%D1%80%D0%BD%D0%B5%D1%82/README.md#%D0%BD%D0%B0%D1%81%D1%82%D1%80%D0%BE%D0%B8%D1%82%D0%B5-%D1%81%D1%82%D0%B0%D1%82%D0%B8%D1%87%D0%B5%D1%81%D0%BA%D0%B8%D0%B9-nat-%D0%B4%D0%BB%D1%8F-r20)
4. [Настроите NAT так, чтобы R19 был доступен с любого узла для удаленного управления.](https://github.com/pekitel/OTUS-Network/blob/main/%D0%94%D0%BE%D0%BC%D0%B0%D1%88%D0%BD%D0%B8%D0%B5%20%D1%80%D0%B0%D0%B1%D0%BE%D1%82%D1%8B/%D0%9F%D1%80%D0%B0%D0%BA%D1%82%D0%B8%D1%87%D0%B5%D1%81%D0%BA%D0%B0%D1%8F%20%D1%80%D0%B0%D0%B1%D0%BE%D1%82%D0%B0/%D0%9E%D1%81%D0%BD%D0%BE%D0%B2%D0%BD%D1%8B%D0%B5%20%D0%BF%D1%80%D0%BE%D1%82%D0%BE%D0%BA%D0%BE%D0%BB%D1%8B%20%D1%81%D0%B5%D1%82%D0%B8%20%D0%B8%D0%BD%D1%82%D0%B5%D1%80%D0%BD%D0%B5%D1%82/README.md#%D0%BD%D0%B0%D1%81%D1%82%D1%80%D0%BE%D0%B8%D1%82%D0%B5-nat-%D1%82%D0%B0%D0%BA-%D1%87%D1%82%D0%BE%D0%B1%D1%8B-r19-%D0%B1%D1%8B%D0%BB-%D0%B4%D0%BE%D1%81%D1%82%D1%83%D0%BF%D0%B5%D0%BD-%D1%81-%D0%BB%D1%8E%D0%B1%D0%BE%D0%B3%D0%BE-%D1%83%D0%B7%D0%BB%D0%B0-%D0%B4%D0%BB%D1%8F-%D1%83%D0%B4%D0%B0%D0%BB%D0%B5%D0%BD%D0%BD%D0%BE%D0%B3%D0%BE-%D1%83%D0%BF%D1%80%D0%B0%D0%B2%D0%BB%D0%B5%D0%BD%D0%B8%D1%8F)
5. [Настроите статический NAT(PAT) для офиса Чокурдах.](https://github.com/pekitel/OTUS-Network/blob/main/%D0%94%D0%BE%D0%BC%D0%B0%D1%88%D0%BD%D0%B8%D0%B5%20%D1%80%D0%B0%D0%B1%D0%BE%D1%82%D1%8B/%D0%9F%D1%80%D0%B0%D0%BA%D1%82%D0%B8%D1%87%D0%B5%D1%81%D0%BA%D0%B0%D1%8F%20%D1%80%D0%B0%D0%B1%D0%BE%D1%82%D0%B0/%D0%9E%D1%81%D0%BD%D0%BE%D0%B2%D0%BD%D1%8B%D0%B5%20%D0%BF%D1%80%D0%BE%D1%82%D0%BE%D0%BA%D0%BE%D0%BB%D1%8B%20%D1%81%D0%B5%D1%82%D0%B8%20%D0%B8%D0%BD%D1%82%D0%B5%D1%80%D0%BD%D0%B5%D1%82/README.md#%D0%BD%D0%B0%D1%81%D1%82%D1%80%D0%BE%D0%B8%D1%82%D0%B5-%D1%81%D1%82%D0%B0%D1%82%D0%B8%D1%87%D0%B5%D1%81%D0%BA%D0%B8%D0%B9-natpat-%D0%B4%D0%BB%D1%8F-%D0%BE%D1%84%D0%B8%D1%81%D0%B0-%D1%87%D0%BE%D0%BA%D1%83%D1%80%D0%B4%D0%B0%D1%85)
6. [Настроите для IPv4 DHCP сервер в офисе Москва на маршрутизаторах R12 и R13. VPC1 и VPC7 должны получать сетевые настройки по DHCP.](https://github.com/pekitel/OTUS-Network/blob/main/%D0%94%D0%BE%D0%BC%D0%B0%D1%88%D0%BD%D0%B8%D0%B5%20%D1%80%D0%B0%D0%B1%D0%BE%D1%82%D1%8B/%D0%9F%D1%80%D0%B0%D0%BA%D1%82%D0%B8%D1%87%D0%B5%D1%81%D0%BA%D0%B0%D1%8F%20%D1%80%D0%B0%D0%B1%D0%BE%D1%82%D0%B0/%D0%9E%D1%81%D0%BD%D0%BE%D0%B2%D0%BD%D1%8B%D0%B5%20%D0%BF%D1%80%D0%BE%D1%82%D0%BE%D0%BA%D0%BE%D0%BB%D1%8B%20%D1%81%D0%B5%D1%82%D0%B8%20%D0%B8%D0%BD%D1%82%D0%B5%D1%80%D0%BD%D0%B5%D1%82/README.md#%D0%BD%D0%B0%D1%81%D1%82%D1%80%D0%BE%D0%B8%D1%82%D0%B5-%D0%B4%D0%BB%D1%8F-ipv4-dhcp-%D1%81%D0%B5%D1%80%D0%B2%D0%B5%D1%80-%D0%B2-%D0%BE%D1%84%D0%B8%D1%81%D0%B5-%D0%BC%D0%BE%D1%81%D0%BA%D0%B2%D0%B0-%D0%BD%D0%B0-%D0%BC%D0%B0%D1%80%D1%88%D1%80%D1%83%D1%82%D0%B8%D0%B7%D0%B0%D1%82%D0%BE%D1%80%D0%B0%D1%85-r12-%D0%B8-r13-vpc1-%D0%B8-vpc7-%D0%B4%D0%BE%D0%BB%D0%B6%D0%BD%D1%8B-%D0%BF%D0%BE%D0%BB%D1%83%D1%87%D0%B0%D1%82%D1%8C-%D1%81%D0%B5%D1%82%D0%B5%D0%B2%D1%8B%D0%B5-%D0%BD%D0%B0%D1%81%D1%82%D1%80%D0%BE%D0%B9%D0%BA%D0%B8-%D0%BF%D0%BE-dhcp)
7. [Настроите NTP сервер на R12 и R13. Все устройства в офисе Москва должны синхронизировать время с R12 и R13.](https://github.com/pekitel/OTUS-Network/blob/main/%D0%94%D0%BE%D0%BC%D0%B0%D1%88%D0%BD%D0%B8%D0%B5%20%D1%80%D0%B0%D0%B1%D0%BE%D1%82%D1%8B/%D0%9F%D1%80%D0%B0%D0%BA%D1%82%D0%B8%D1%87%D0%B5%D1%81%D0%BA%D0%B0%D1%8F%20%D1%80%D0%B0%D0%B1%D0%BE%D1%82%D0%B0/%D0%9E%D1%81%D0%BD%D0%BE%D0%B2%D0%BD%D1%8B%D0%B5%20%D0%BF%D1%80%D0%BE%D1%82%D0%BE%D0%BA%D0%BE%D0%BB%D1%8B%20%D1%81%D0%B5%D1%82%D0%B8%20%D0%B8%D0%BD%D1%82%D0%B5%D1%80%D0%BD%D0%B5%D1%82/README.md#%D0%BD%D0%B0%D1%81%D1%82%D1%80%D0%BE%D0%B8%D1%82%D0%B5-ntp-%D1%81%D0%B5%D1%80%D0%B2%D0%B5%D1%80-%D0%BD%D0%B0-r12-%D0%B8-r13-%D0%B2%D1%81%D0%B5-%D1%83%D1%81%D1%82%D1%80%D0%BE%D0%B9%D1%81%D1%82%D0%B2%D0%B0-%D0%B2-%D0%BE%D1%84%D0%B8%D1%81%D0%B5-%D0%BC%D0%BE%D1%81%D0%BA%D0%B2%D0%B0-%D0%B4%D0%BE%D0%BB%D0%B6%D0%BD%D1%8B-%D1%81%D0%B8%D0%BD%D1%85%D1%80%D0%BE%D0%BD%D0%B8%D0%B7%D0%B8%D1%80%D0%BE%D0%B2%D0%B0%D1%82%D1%8C-%D0%B2%D1%80%D0%B5%D0%BC%D1%8F-%D1%81-r12-%D0%B8-r13)
8. [Все офисы в лабораторной работе должны иметь IP связность.](https://github.com/pekitel/OTUS-Network/blob/main/%D0%94%D0%BE%D0%BC%D0%B0%D1%88%D0%BD%D0%B8%D0%B5%20%D1%80%D0%B0%D0%B1%D0%BE%D1%82%D1%8B/%D0%9F%D1%80%D0%B0%D0%BA%D1%82%D0%B8%D1%87%D0%B5%D1%81%D0%BA%D0%B0%D1%8F%20%D1%80%D0%B0%D0%B1%D0%BE%D1%82%D0%B0/%D0%9E%D1%81%D0%BD%D0%BE%D0%B2%D0%BD%D1%8B%D0%B5%20%D0%BF%D1%80%D0%BE%D1%82%D0%BE%D0%BA%D0%BE%D0%BB%D1%8B%20%D1%81%D0%B5%D1%82%D0%B8%20%D0%B8%D0%BD%D1%82%D0%B5%D1%80%D0%BD%D0%B5%D1%82/README.md#%D0%B2%D1%81%D0%B5-%D0%BE%D1%84%D0%B8%D1%81%D1%8B-%D0%B2-%D0%BB%D0%B0%D0%B1%D0%BE%D1%80%D0%B0%D1%82%D0%BE%D1%80%D0%BD%D0%BE%D0%B9-%D1%80%D0%B0%D0%B1%D0%BE%D1%82%D0%B5-%D0%B4%D0%BE%D0%BB%D0%B6%D0%BD%D1%8B-%D0%B8%D0%BC%D0%B5%D1%82%D1%8C-ip-%D1%81%D0%B2%D1%8F%D0%B7%D0%BD%D0%BE%D1%81%D1%82%D1%8C)

## Карта сети

>![карта_new](https://user-images.githubusercontent.com/112701413/215788614-81ee7bd2-739a-4ef4-b113-8dc675d212f3.jpg)


##### Настроите NAT(PAT) на R14 и R15. Трансляция должна осуществляться в адрес автономной системы AS1001.

**R14**

```
R14>en
R14#conf t
R14(config)#interface Ethernet0/0
R14(config-if)#ip nat inside
R14(config-if)#interface Ethernet0/1
R14(config-if)#ip nat inside
R14(config-if)#interface Ethernet0/2
R14(config-if)#ip nat outside
R14(config-if)#interface Ethernet0/3
R14(config-if)#ip nat inside
R14(config-if)#interface Ethernet1/0
R14(config-if)#ip nat inside
R14(config-if)#exit
//указываем на какой ip будем транслировать внутренние ip адреса локальной сети://
R14(config)#ip nat pool OVRLD 77.37.144.14 77.37.144.14 netmask 255.255.255.0
//включаем PAT://
R14(config)#ip nat inside source list 10 pool OVRLD overload 
//указываем пул внутренних ip адресов, которые будем транслировать://
R14(config)#access-list 10 permit 172.16.3.0 0.0.0.15
```

**R15**

```
R15>en
R15#conf t
R15(config)#interface Ethernet0/0
R15(config-if)#ip nat inside
R15(config-if)#interface Ethernet0/1
R15(config-if)#ip nat inside
R15(config-if)#interface Ethernet0/2
R15(config-if)#ip nat outside
R15(config-if)#interface Ethernet0/3
R15(config-if)#ip nat inside
R15(config-if)#interface Ethernet1/0
R15(config-if)#ip nat inside
R15(config-if)#exit
//указываем на какой ip будем транслировать внутренние ip адреса локальной сети://
R15(config)#ip nat pool OVRLD 77.37.144.15 77.37.144.15 netmask 255.255.255.0
//включаем PAT://
R15(config)#ip nat inside source list 10 pool OVRLD overload 
//указываем пул внутренних ip адресов, которые будем транслировать://
R15(config)#access-list 10 permit 172.16.3.16 0.0.0.15
```

##### Настроите NAT(PAT) на R18. Трансляция должна осуществляться в пул из 5 адресов автономной системы AS2042.

**R18**

```
R18>en
R18#conf t
R18(config)#interface Ethernet0/2
R18(config-if)#ip nat outside
R18(config-if)#interface Ethernet0/3
R18(config-if)#ip nat outside
R18(config-if)#interface Ethernet0/0
R18(config-if)#ip nat inside
R18(config-if)#interface Ethernet0/1
R18(config-if)#ip nat inside
R18(config-if)#exit
// указываем пул внутренних ip адресов, которые будем транслировать:
R18(config)#access-list 10 permit 172.16.1.0 0.0.0.15
R18(config)#access-list 10 permit 172.16.1.16 0.0.0.15
// указываем на какие ip будем транслировать внутренние ip адреса локальной сети:
R18(config)#ip nat pool OVRLD 33.72.66.10 33.72.66.14 netmask 255.255.255.0
//Вкл самого NAT
R18(config)#ip nat inside source list 10 pool OVRLD overload
```

##### Настроите статический NAT для R20.

**R14**

```
R14>en
R14#conf t
R14(config)#ip nat inside source static 100.100.1.20 77.37.144.20
```

**R15**

```
R15>en
R15#conf t
R15(config)#ip nat inside source static 100.100.1.20 77.37.144.20
```

##### Настроите NAT так, чтобы R19 был доступен с любого узла для удаленного управления.

**R14**

```
R14>en
R14#conf t
R14(config)#ip nat inside source static tcp 100.100.1.19 22 77.37.144.19 22 extendable
```

**R15**

```
R15>en
R15#conf t
R15(config)#ip nat inside source static tcp 100.100.1.19 22 77.37.144.19 22 extendable
```

**R19**

```
R19>en
R19#conf t
R19(config)#ip domain-name R19
R19(config)#crypto key generate rsa
The name for the keys will be: R19.R19
Choose the size of the key modulus in the range of 360 to 4096 for your
  General Purpose Keys. Choosing a key modulus greater than 512 may take
  a few minutes.

How many bits in the modulus [512]: 1024
% Generating 1024 bit RSA keys, keys will be non-exportable...
[OK] (elapsed time was 0 seconds)

R19(config)#line vty 0 4
R19(config-line)#transport input ssh
R19(config-line)#login local
R19(config-line)#username admin secret cisco
R19(config)#ip ssh version 2
R19(config)#enable secret cisco
R19(config)#exit
R19#wr
Building configuration...
[OK]
R19#
```
***проверим через роутер R27***

>![R19_ssh](https://user-images.githubusercontent.com/112701413/215788064-40bbe2c0-5b43-41e7-8f31-e690c5bcab96.jpg)



##### Настроите статический NAT(PAT) для офиса Чокурдах.

**R28**

```
R28>en
R28#conf t
R28(config)#interface ethernet 0/0
R28(config-if)#ip nat outside
R28(config-if)#exit
R28(config)#interface ethernet 0/1
R28(config-if)#ip nat outside
R28(config-if)#exit
R28(config)#interface ethernet 0/2.10
R28(config-subif)#ip nat inside
R28(config-subif)#exit
R28(config)#interface ethernet 0/2.20
R28(config-subif)#ip nat inside
R28(config-subif)#exit
R28(config)#ip nat inside source static 172.16.2.18 109.72.67.2
R28(config)#ip nat inside source static 172.16.2.2 109.72.67.3
R28(config)#exit
R28#wr
```

**R26**

```
R26>en
R26#conf t
R26(config)#router bgp 520
R26(config-router)#address-family ipv4
R26(config-router-af)#network 109.72.67.0 mask 255.255.255.248
R26(config-router-af)#end
R26#conf t
R26(config)#ip route 109.72.67.0 255.255.255.248 109.72.1.34
R26(config)#exit
R26#wr
```

**R25**

```
R25>en
R25#conf t
R25(config)#router bgp 520
R25(config-router)#address-family ipv4
R25(config-router-af)#network 109.72.67.0 mask 255.255.255.248
R25(config-router-af)#end
R25#conf t
R25(config)#ip route 109.72.67.0 255.255.255.248 109.72.1.30
R25(config)#exit
R25#wr
```

**VPC30**

```
VPCS> ip 172.16.2.2 255.255.255.240 172.16.2.1
Checking for duplicate address...
VPCS : 172.16.2.2 255.255.255.240 gateway 172.16.2.1

VPCS> save
Saving startup configuration to startup.vpc
.  done
```

**VPC31**

```
VPCS> ip 172.16.2.18 255.255.255.240 172.16.2.17
Checking for duplicate address...
VPCS : 172.16.2.18 255.255.255.240 gateway 172.16.2.17

VPCS> save
Saving startup configuration to startup.vpc
.  done
```

***Проверка работоспособности схемы***

```
R25#ping 109.72.67.2
Type escape sequence to abort.
Sending 5, 100-byte ICMP Echos to 109.72.67.2, timeout is 2 seconds:
!!!!!
Success rate is 100 percent (5/5), round-trip min/avg/max = 1/1/2 ms
R25#ping 109.72.67.3
Type escape sequence to abort.
Sending 5, 100-byte ICMP Echos to 109.72.67.3, timeout is 2 seconds:
!!!!!
Success rate is 100 percent (5/5), round-trip min/avg/max = 1/1/2 ms
```

##### Настроите для IPv4 DHCP сервер в офисе Москва на маршрутизаторах R12 и R13. VPC1 и VPC7 должны получать сетевые настройки по DHCP.

**R12**

```
R12>en
R12#conf t
R12(config)#ip dhcp pool VPC1
R12(dhcp-config)#network 172.16.3.0 255.255.255.240
R12(dhcp-config)#dns-server 8.8.8.8 
R12(dhcp-config)#default-router 172.16.3.1 
R12(dhcp-config)#exit
R12(config)#ip dhcp excluded-address 172.16.3.1
R12(config)#ipv6 dhcp pool VPC1
R12(config-dhcpv6)#address prefix 2001:ABCD:EEBB:AAAA:2222::1/80
R12(config-dhcpv6)#dns-server 2A02:6B8::FEED:FF
R12(config-dhcpv6)#domain-name msk1.ru
R12(config-dhcpv6)#exit
R12(config)#do wr

```

**R13**

```
R13>en
R13#conf t
R13(config)#ip dhcp pool VPC7
R13(dhcp-config)#network 172.16.3.16 255.255.255.240
R13(dhcp-config)#dns-server 8.8.8.8 
R13(dhcp-config)#default-router 172.16.3.17 
R13(dhcp-config)#exit
R13(config)#ip dhcp excluded-address 172.16.3.17
R13(config)#ipv6 dhcp pool VPC7
R13(config-dhcpv6)#address prefix 2001:ABCD:EEBB:AAAA:3333::1/80
R13(config-dhcpv6)#dns-server 2A02:6B8::FEED:FF
R13(config-dhcpv6)#domain-name msk2.ru
R13(config-dhcpv6)#exit
R13(config)#do wr
```

##### Настроите NTP сервер на R12 и R13. Все устройства в офисе Москва должны синхронизировать время с R12 и R13.

**R12**

```
R12>en
R12#conf t
R12(config)#interface Ethernet0/2
R12(config-if)#ntp broadcast
R12(config-if)#exit
R12(config)#interface Ethernet0/3
R12(config-if)#ntp broadcast
R12(config-if)#exit
R12(config)#ntp source Loopback12
R12(config)#ntp master 5
R12(config)#ntp update-calendar
```

**R13**

```
R13>en
R13#conf t
R13(config)#interface Ethernet0/2
R13(config-if)#ntp broadcast
R13(config-if)#exit
R13(config)#interface Ethernet0/3
R13(config-if)#ntp broadcast
R13(config-if)#exit
R13(config)#ntp source Loopback13
R13(config)#ntp master 5
R13(config)#ntp update-calendar
```

**R14**

```
R14>en
R14#conf t
R14(config)#interface Ethernet0/0
R14(config-if)#ntp broadcast client
R14(config-if)#exit
R14(config)#interface Ethernet0/1
R14(config-if)#ntp broadcast client
R14(config-if)#exit
R14(config)#ntp server 100.100.1.12
R14(config)#ntp server 100.100.1.13
R14(config)#exit
R14#wr
R14#show ntp associations 

  address         ref clock       st   when   poll reach  delay  offset   disp
+~100.100.1.12    127.127.1.1      5    228    256   377  0.000   0.000  2.252
*~100.100.1.13    127.127.1.1      5     90    256   377  0.000   0.000  2.862
 * sys.peer, # selected, + candidate, - outlyer, x falseticker, ~ configured
```

**R15**

```
R15>en
R15#conf t
R15(config)#interface Ethernet0/0
R15(config-if)#ntp broadcast client
R15(config-if)#exit
R15(config)#interface Ethernet0/1
R15(config-if)#ntp broadcast client
R15(config-if)#exit
R15(config)#ntp server 100.100.1.12
R15(config)#ntp server 100.100.1.13
R15(config)#exit
R15#wr
R15#show ntp associations 

  address         ref clock       st   when   poll reach  delay  offset   disp
+~100.100.1.12    127.127.1.1      5     37     64   377  1.000  -0.500  2.888
+~100.100.1.13    127.127.1.1      5      5     64   377  0.000   0.000  3.129
 * sys.peer, # selected, + candidate, - outlyer, x falseticker, ~ configured
```

**19**

```
R19>en
R19#conf t
R19(config)#interface Ethernet0/0
R19(config-if)#ntp broadcast client
R19(config-if)#exit
R19(config)#ntp server 100.100.1.12
R19(config)#ntp server 100.100.1.13
R19(config)#exit
R19#wr
R19#show ntp associations 

  address         ref clock       st   when   poll reach  delay  offset   disp
+~100.100.1.12    127.127.1.1      5    951   1024   377  0.000   0.000  2.033
*~100.100.1.13    127.127.1.1      5    754   1024   377  0.000   0.000  2.084
 * sys.peer, # selected, + candidate, - outlyer, x falseticker, ~ configured
```

**R20**

```
R20>en
R20#conf t
R20(config)#interface Ethernet0/0
R20(config-if)#ntp broadcast client
R20(config-if)#exit
R20(config)#ntp server 100.100.1.12
R20(config)#ntp server 100.100.1.13
R20(config)#exit
R20#wr
R20#show ntp associations 

  address         ref clock       st   when   poll reach  delay  offset   disp
*~100.100.1.12    127.127.1.1      5    114   1024   377  0.000   0.000  2.072
+~100.100.1.13    127.127.1.1      5    358   1024   377  1.000   0.500  1.974
 * sys.peer, # selected, + candidate, - outlyer, x falseticker, ~ configured
```

***А теперь свичи:SW2 / SW3 / SW4 / SW5***

Тут в роли NTP сервера будет GW вилана

**SW2**

```
SW2>en
SW2#conf t
SW2(config)#ntp server 172.16.30.1
SW2(config)#end
SW2#show ntp associations 

  address         ref clock       st   when   poll reach  delay  offset   disp
*~172.16.30.1     127.127.1.1      5     46     64   377  2.000   0.000  4.058
 * sys.peer, # selected, + candidate, - outlyer, x falseticker, ~ configured
```
***Аналогичным образом настраивает SW3 / SW4 / SW5***

##### Все офисы в лабораторной работе должны иметь IP связность.

**Проверим с R14**

```
R14>en
R14#ping 109.72.1.26
Type escape sequence to abort.
Sending 5, 100-byte ICMP Echos to 109.72.1.26, timeout is 2 seconds:
!!!!!
Success rate is 100 percent (5/5), round-trip min/avg/max = 1/1/2 ms
R14#ping 109.72.1.30
Type escape sequence to abort.
Sending 5, 100-byte ICMP Echos to 109.72.1.30, timeout is 2 seconds:
!!!!!
Success rate is 100 percent (5/5), round-trip min/avg/max = 1/1/1 ms
R14#ping 109.72.1.34
Type escape sequence to abort.
Sending 5, 100-byte ICMP Echos to 109.72.1.34, timeout is 2 seconds:
!!!!!
Success rate is 100 percent (5/5), round-trip min/avg/max = 1/1/1 ms
R14#ping 109.72.1.38
Type escape sequence to abort.
Sending 5, 100-byte ICMP Echos to 109.72.1.38, timeout is 2 seconds:
!!!!!
Success rate is 100 percent (5/5), round-trip min/avg/max = 1/1/1 ms
R14#ping 109.72.1.42
Type escape sequence to abort.
Sending 5, 100-byte ICMP Echos to 109.72.1.42, timeout is 2 seconds:
!!!!!
Success rate is 100 percent (5/5), round-trip min/avg/max = 1/1/1 ms
R14#
```
