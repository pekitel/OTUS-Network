# Задание

## Настроить DHCP в офисе Москва
## Настроить синхронизацию времени в офисе Москва
## Настроить NAT в офисе Москва, C.-Перетбруг и Чокурдах

1. Настроите NAT(PAT) на R14 и R15. Трансляция должна осуществляться в адрес автономной системы AS1001.
2. Настроите NAT(PAT) на R18. Трансляция должна осуществляться в пул из 5 адресов автономной системы AS2042.
3. Настроите статический NAT для R20.
4. Настроите NAT так, чтобы R19 был доступен с любого узла для удаленного управления.
5. Настроите статический NAT(PAT) для офиса Чокурдах.
6. Настроите для IPv4 DHCP сервер в офисе Москва на маршрутизаторах R12 и R13. VPC1 и VPC7 должны получать сетевые настройки по DHCP.
7. Настроите NTP сервер на R12 и R13. Все устройства в офисе Москва должны синхронизировать время с R12 и R13.
8. Все офисы в лабораторной работе должны иметь IP связность.

## Карта сети
![карта](https://user-images.githubusercontent.com/112701413/214368302-4736c16b-2152-4cf1-8246-18163acf68bd.jpg)


##### Настроите NAT(PAT) на R14 и R15. Трансляция должна осуществляться в адрес автономной системы AS1001.
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
##### Все офисы в лабораторной работе должны иметь IP связность.
