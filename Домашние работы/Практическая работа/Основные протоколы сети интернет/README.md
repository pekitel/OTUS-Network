# Задание

## Настроить DHCP в офисе Москва
## Настроить синхронизацию времени в офисе Москва
## Настроить NAT в офисе Москва, C.-Перетбруг и Чокурдах

1. Настроите NAT(PAT) на R14 и R15. Трансляция должна осуществляться в адрес автономной системы AS1001.
2. Настроите NAT(PAT) на R18. Трансляция должна осуществляться в пул из 5 адресов автономной системы AS2042.
3. Настроите статический NAT для R20.
4. Настроите NAT так, чтобы R19 был доступен с любого узла для удаленного управления.
5. Настроите статический NAT(PAT) для офиса Чокурдах.
6. [Настроите для IPv4 DHCP сервер в офисе Москва на маршрутизаторах R12 и R13. VPC1 и VPC7 должны получать сетевые настройки по DHCP.](https://github.com/pekitel/OTUS-Network/blob/main/%D0%94%D0%BE%D0%BC%D0%B0%D1%88%D0%BD%D0%B8%D0%B5%20%D1%80%D0%B0%D0%B1%D0%BE%D1%82%D1%8B/%D0%9F%D1%80%D0%B0%D0%BA%D1%82%D0%B8%D1%87%D0%B5%D1%81%D0%BA%D0%B0%D1%8F%20%D1%80%D0%B0%D0%B1%D0%BE%D1%82%D0%B0/%D0%9E%D1%81%D0%BD%D0%BE%D0%B2%D0%BD%D1%8B%D0%B5%20%D0%BF%D1%80%D0%BE%D1%82%D0%BE%D0%BA%D0%BE%D0%BB%D1%8B%20%D1%81%D0%B5%D1%82%D0%B8%20%D0%B8%D0%BD%D1%82%D0%B5%D1%80%D0%BD%D0%B5%D1%82/README.md#%D0%BD%D0%B0%D1%81%D1%82%D1%80%D0%BE%D0%B8%D1%82%D0%B5-%D0%B4%D0%BB%D1%8F-ipv4-dhcp-%D1%81%D0%B5%D1%80%D0%B2%D0%B5%D1%80-%D0%B2-%D0%BE%D1%84%D0%B8%D1%81%D0%B5-%D0%BC%D0%BE%D1%81%D0%BA%D0%B2%D0%B0-%D0%BD%D0%B0-%D0%BC%D0%B0%D1%80%D1%88%D1%80%D1%83%D1%82%D0%B8%D0%B7%D0%B0%D1%82%D0%BE%D1%80%D0%B0%D1%85-r12-%D0%B8-r13-vpc1-%D0%B8-vpc7-%D0%B4%D0%BE%D0%BB%D0%B6%D0%BD%D1%8B-%D0%BF%D0%BE%D0%BB%D1%83%D1%87%D0%B0%D1%82%D1%8C-%D1%81%D0%B5%D1%82%D0%B5%D0%B2%D1%8B%D0%B5-%D0%BD%D0%B0%D1%81%D1%82%D1%80%D0%BE%D0%B9%D0%BA%D0%B8-%D0%BF%D0%BE-dhcp)
7. [Настроите NTP сервер на R12 и R13. Все устройства в офисе Москва должны синхронизировать время с R12 и R13.](https://github.com/pekitel/OTUS-Network/blob/main/%D0%94%D0%BE%D0%BC%D0%B0%D1%88%D0%BD%D0%B8%D0%B5%20%D1%80%D0%B0%D0%B1%D0%BE%D1%82%D1%8B/%D0%9F%D1%80%D0%B0%D0%BA%D1%82%D0%B8%D1%87%D0%B5%D1%81%D0%BA%D0%B0%D1%8F%20%D1%80%D0%B0%D0%B1%D0%BE%D1%82%D0%B0/%D0%9E%D1%81%D0%BD%D0%BE%D0%B2%D0%BD%D1%8B%D0%B5%20%D0%BF%D1%80%D0%BE%D1%82%D0%BE%D0%BA%D0%BE%D0%BB%D1%8B%20%D1%81%D0%B5%D1%82%D0%B8%20%D0%B8%D0%BD%D1%82%D0%B5%D1%80%D0%BD%D0%B5%D1%82/README.md#%D0%BD%D0%B0%D1%81%D1%82%D1%80%D0%BE%D0%B8%D1%82%D0%B5-ntp-%D1%81%D0%B5%D1%80%D0%B2%D0%B5%D1%80-%D0%BD%D0%B0-r12-%D0%B8-r13-%D0%B2%D1%81%D0%B5-%D1%83%D1%81%D1%82%D1%80%D0%BE%D0%B9%D1%81%D1%82%D0%B2%D0%B0-%D0%B2-%D0%BE%D1%84%D0%B8%D1%81%D0%B5-%D0%BC%D0%BE%D1%81%D0%BA%D0%B2%D0%B0-%D0%B4%D0%BE%D0%BB%D0%B6%D0%BD%D1%8B-%D1%81%D0%B8%D0%BD%D1%85%D1%80%D0%BE%D0%BD%D0%B8%D0%B7%D0%B8%D1%80%D0%BE%D0%B2%D0%B0%D1%82%D1%8C-%D0%B2%D1%80%D0%B5%D0%BC%D1%8F-%D1%81-r12-%D0%B8-r13)
8. Все офисы в лабораторной работе должны иметь IP связность.

## Карта сети
![карта](https://user-images.githubusercontent.com/112701413/214368302-4736c16b-2152-4cf1-8246-18163acf68bd.jpg)


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
##### Настроите статический NAT для R20.
##### Настроите NAT так, чтобы R19 был доступен с любого узла для удаленного управления.
##### Настроите статический NAT(PAT) для офиса Чокурдах.
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
