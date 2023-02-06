# Задание

1. [Настроите GRE поверх IPSec между офисами Москва и С.-Петербург.](https://github.com/pekitel/OTUS-Network/blob/main/%D0%94%D0%BE%D0%BC%D0%B0%D1%88%D0%BD%D0%B8%D0%B5%20%D1%80%D0%B0%D0%B1%D0%BE%D1%82%D1%8B/%D0%9F%D1%80%D0%B0%D0%BA%D1%82%D0%B8%D1%87%D0%B5%D1%81%D0%BA%D0%B0%D1%8F%20%D1%80%D0%B0%D0%B1%D0%BE%D1%82%D0%B0/%D0%92%D0%B8%D1%80%D1%82%D1%83%D0%B0%D0%BB%D1%8C%D0%BD%D0%B0%D1%8F%20%D1%87%D0%B0%D1%81%D1%82%D0%BD%D1%8B%D0%B5%20%D1%81%D0%B5%D1%82%D0%B8%20-%20VPN%20IPSec%20over%20DmVPN/README.md#%D0%BD%D0%B0%D1%81%D1%82%D1%80%D0%BE%D0%B8%D1%82%D0%B5-gre-%D0%BF%D0%BE%D0%B2%D0%B5%D1%80%D1%85-ipsec-%D0%BC%D0%B5%D0%B6%D0%B4%D1%83-%D0%BE%D1%84%D0%B8%D1%81%D0%B0%D0%BC%D0%B8-%D0%BC%D0%BE%D1%81%D0%BA%D0%B2%D0%B0-%D0%B8-%D1%81-%D0%BF%D0%B5%D1%82%D0%B5%D1%80%D0%B1%D1%83%D1%80%D0%B3)
2. [Настроите DMVPN поверх IPSec между Москва и Чокурдах, Лабытнанги.](https://github.com/pekitel/OTUS-Network/blob/main/%D0%94%D0%BE%D0%BC%D0%B0%D1%88%D0%BD%D0%B8%D0%B5%20%D1%80%D0%B0%D0%B1%D0%BE%D1%82%D1%8B/%D0%9F%D1%80%D0%B0%D0%BA%D1%82%D0%B8%D1%87%D0%B5%D1%81%D0%BA%D0%B0%D1%8F%20%D1%80%D0%B0%D0%B1%D0%BE%D1%82%D0%B0/%D0%92%D0%B8%D1%80%D1%82%D1%83%D0%B0%D0%BB%D1%8C%D0%BD%D0%B0%D1%8F%20%D1%87%D0%B0%D1%81%D1%82%D0%BD%D1%8B%D0%B5%20%D1%81%D0%B5%D1%82%D0%B8%20-%20VPN%20IPSec%20over%20DmVPN/README.md#%D0%BD%D0%B0%D1%81%D1%82%D1%80%D0%BE%D0%B8%D1%82%D0%B5-dmvpn-%D0%BF%D0%BE%D0%B2%D0%B5%D1%80%D1%85-ipsec-%D0%BC%D0%B5%D0%B6%D0%B4%D1%83-%D0%BC%D0%BE%D1%81%D0%BA%D0%B2%D0%B0-%D0%B8-%D1%87%D0%BE%D0%BA%D1%83%D1%80%D0%B4%D0%B0%D1%85-%D0%BB%D0%B0%D0%B1%D1%8B%D1%82%D0%BD%D0%B0%D0%BD%D0%B3%D0%B8)
3. [Все узлы в офисах в лабораторной работе должны иметь IP связность.](https://github.com/pekitel/OTUS-Network/tree/main/%D0%94%D0%BE%D0%BC%D0%B0%D1%88%D0%BD%D0%B8%D0%B5%20%D1%80%D0%B0%D0%B1%D0%BE%D1%82%D1%8B/%D0%9F%D1%80%D0%B0%D0%BA%D1%82%D0%B8%D1%87%D0%B5%D1%81%D0%BA%D0%B0%D1%8F%20%D1%80%D0%B0%D0%B1%D0%BE%D1%82%D0%B0/%D0%92%D0%B8%D1%80%D1%82%D1%83%D0%B0%D0%BB%D1%8C%D0%BD%D0%B0%D1%8F%20%D1%87%D0%B0%D1%81%D1%82%D0%BD%D1%8B%D0%B5%20%D1%81%D0%B5%D1%82%D0%B8%20-%20VPN%20IPSec%20over%20DmVPN#%D0%B2%D1%81%D0%B5-%D1%83%D0%B7%D0%BB%D1%8B-%D0%B2-%D0%BE%D1%84%D0%B8%D1%81%D0%B0%D1%85-%D0%B2-%D0%BB%D0%B0%D0%B1%D0%BE%D1%80%D0%B0%D1%82%D0%BE%D1%80%D0%BD%D0%BE%D0%B9-%D1%80%D0%B0%D0%B1%D0%BE%D1%82%D0%B5-%D0%B4%D0%BE%D0%BB%D0%B6%D0%BD%D1%8B-%D0%B8%D0%BC%D0%B5%D1%82%D1%8C-ip-%D1%81%D0%B2%D1%8F%D0%B7%D0%BD%D0%BE%D1%81%D1%82%D1%8C)

## Карта сети

>![карта_new](https://user-images.githubusercontent.com/112701413/216961659-c65f68b6-6271-4fe9-be66-5f39223af3ec.jpg)

### Настроите GRE поверх IPSec между офисами Москва и С.-Петербург.

**R14**

```
R14>en
R14#conf t
R14(config)#interface tunnel 100
R14(config-if)#ip address 10.10.10.1 255.255.255.252
R14(config-if)#ip mtu 1400
R14(config-if)#ip tcp adjust-mss 1360
R14(config-if)#tunnel source 82.138.2.2
R14(config-if)#tunnel destination 109.72.1.38
R14(config-if)#exit
R14(config)#exit
R14(config)#crypto isakmp policy 1
R14(config-isakmp)#encryption 3des 
R14(config-isakmp)#hash md5 
R14(config-isakmp)#authentication pre-share 
R14(config-isakmp)#group 2
R14(config-isakmp)#lifetime 86400
R14(config-isakmp)#exit
R14(config)#crypto isakmp key qwerty1234 address 109.72.1.38
R14(config)#crypto ipsec transform-set MSK esp-3des esp-md5-hmac
R14(cfg-crypto-trans)#mode transport 
R14(cfg-crypto-trans)#exit
R14(config)#crypto ipsec profile MOSCOW
R14(ipsec-profile)#set security-association lifetime seconds 86400
R14(ipsec-profile)#set transform-set MSK
R14(ipsec-profile)#exit
R14(config)#interface Tunnel100
R14(config-if)#tunnel protection ipsec profile MOSCOW
R14(config-if)#end 
R14#wr
```
```
R14#show crypto session 
Crypto session current status

Interface: Tunnel100
Session status: UP-ACTIVE     
Peer: 109.72.1.38 port 500 
  IKEv1 SA: local 82.138.2.2/500 remote 109.72.1.38/500 Active 
  IPSEC FLOW: permit 47 host 82.138.2.2 host 109.72.1.38 
        Active SAs: 2, origin: crypto map
```

**R18**

```
R18>en
R18#conf t
R18(config)#interface tunnel 100
R18(config-if)#ip address 10.10.10.2 255.255.255.252
R18(config-if)#ip mtu 1400
R18(config-if)#ip tcp adjust-mss 1360
R18(config-if)#tunnel source 109.72.1.38
R18(config-if)#tunnel destination 82.138.2.2
R18(config-if)#exit
R18(config)#exit
R18(config)#crypto isakmp policy 1
R18(config-isakmp)#encryption 3des 
R18(config-isakmp)#hash md5 
R18(config-isakmp)#authentication pre-share 
R18(config-isakmp)#group 2
R18(config-isakmp)#lifetime 86400
R18(config-isakmp)#exit
R18(config)#crypto isakmp key qwerty1234 address 82.138.2.2
R18(config)#crypto ipsec transform-set MSK esp-3des esp-md5-hmac
R18(cfg-crypto-trans)#mode transport 
R18(cfg-crypto-trans)#exit
R18(config)#crypto ipsec profile MOSCOW
R18(ipsec-profile)#set security-association lifetime seconds 86400
R18(ipsec-profile)#set transform-set MSK
R18(ipsec-profile)#exit
R18(config)#interface Tunnel100
R18(config-if)#tunnel protection ipsec profile MOSCOW
R18(config-if)#end 
R18#wr
```
```
R18#show crypto session 
Crypto session current status

Interface: Tunnel100
Session status: UP-ACTIVE     
Peer: 82.138.2.2 port 500 
  IKEv1 SA: local 109.72.1.38/500 remote 82.138.2.2/500 Active 
  IPSEC FLOW: permit 47 host 109.72.1.38 host 82.138.2.2 
        Active SAs: 2, origin: crypto map
```

****Проверка****

**R14**

```
R14#ping 10.10.10.1
Type escape sequence to abort.
Sending 5, 100-byte ICMP Echos to 10.10.10.1, timeout is 2 seconds:
!!!!!
Success rate is 100 percent (5/5), round-trip min/avg/max = 4/4/5 ms
R14#ping 10.10.10.2
Type escape sequence to abort.
Sending 5, 100-byte ICMP Echos to 10.10.10.2, timeout is 2 seconds:
!!!!!
Success rate is 100 percent (5/5), round-trip min/avg/max = 5/5/6 ms
```

**R18**

```
R18#ping 10.10.10.1
Type escape sequence to abort.
Sending 5, 100-byte ICMP Echos to 10.10.10.1, timeout is 2 seconds:
!!!!!
Success rate is 100 percent (5/5), round-trip min/avg/max = 5/5/6 ms
R18#ping 10.10.10.2
Type escape sequence to abort.
Sending 5, 100-byte ICMP Echos to 10.10.10.2, timeout is 2 seconds:
!!!!!
Success rate is 100 percent (5/5), round-trip min/avg/max = 4/4/5 ms
```

### Настроите DMVPN поверх IPSec между Москва и Чокурдах, Лабытнанги.
### Все узлы в офисах в лабораторной работе должны иметь IP связность.
