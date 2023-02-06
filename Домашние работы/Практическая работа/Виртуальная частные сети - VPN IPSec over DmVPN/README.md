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

**R15**

```
R15>en
R15#conf t
R15(config)#interface Tunnel100
R15(config-if)#ip address 10.20.20.1 255.255.255.0
R15(config-if)#no ip redirects
R15(config-if)#ip mtu 1440
R15(config-if)#ip nhrp authentication MSK
R15(config-if)#ip nhrp map multicast dynamic
R15(config-if)#ip nhrp network-id 1
R15(config-if)#load-interval 30
R15(config-if)#keepalive 5 10
R15(config-if)#tunnel source 77.94.165.2
R15(config-if)#tunnel mode gre multipoint
R15(config-if)#exit
R15(config)#crypto isakmp policy 1
R15(config-isakmp)#encryption 3des 
R15(config-isakmp)#hash md5 
R15(config-isakmp)#authentication pre-share 
R15(config-isakmp)#group 2
R15(config-isakmp)#exit
R15(config)#crypto isakmp key qwerty1234 address 0.0.0.0
R15(config)#crypto ipsec transform-set MSK esp-3des esp-md5-hmac 
R15(cfg-crypto-trans)#mode tunnel 
R15(cfg-crypto-trans)#exit
R15(config)#crypto ipsec profile MOSCOW
R15(ipsec-profile)#set security-association lifetime seconds 86400
R15(ipsec-profile)#set transform-set MSK
R15(ipsec-profile)#exit
R15(config)#interface tunnel 100
R15(config-if)#tunnel protection ipsec profile MOSCOW
```
```
R15#show crypto isakmp sa 
IPv4 Crypto ISAKMP SA
dst             src             state          conn-id status
77.94.165.2     109.72.1.34     QM_IDLE           1008 ACTIVE
77.94.165.2     109.72.1.26     QM_IDLE           1007 ACTIVE

IPv6 Crypto ISAKMP SA


R15#show dmvpn
Legend: Attrb --> S - Static, D - Dynamic, I - Incomplete
        N - NATed, L - Local, X - No Socket
        # Ent --> Number of NHRP entries with same NBMA peer
        NHS Status: E --> Expecting Replies, R --> Responding, W --> Waiting
        UpDn Time --> Up or Down Time for a Tunnel
==========================================================================

Interface: Tunnel100, IPv4 NHRP Details 
Type:Hub, NHRP Peers:2, 

 # Ent  Peer NBMA Addr Peer Tunnel Add State  UpDn Tm Attrb
 ----- --------------- --------------- ----- -------- -----
     1 109.72.1.26          10.20.20.2    UP    3d01h     D
     1 109.72.1.34          10.20.20.3    UP    3d01h     D
```
**R27**

```
R27>en
R27#conf t
R27(config)#interface Tunnel100
R27(config-if)#ip address 10.20.20.2 255.255.255.0
R27(config-if)#no ip redirects
R27(config-if)#ip mtu 1440
R27(config-if)#ip nhrp authentication MSK
R27(config-if)#ip nhrp map multicast dynamic
R27(config-if)#ip nhrp map 10.20.20.1 77.94.165.2
R27(config-if)#ip nhrp map multicast 77.94.165.2
R27(config-if)#ip nhrp network-id 1
R27(config-if)#ip nhrp nhs 10.20.20.1
R27(config-if)#ip nhrp registration no-unique
R27(config-if)#load-interval 30
R27(config-if)#keepalive 5 10
R27(config-if)#tunnel source Ethernet0/0
R27(config-if)#tunnel mode gre multipoint
R27(config-if)#exit
R27(config)#crypto isakmp policy 1
R27(config-isakmp)#encryption 3des 
R27(config-isakmp)#hash md5 
R27(config-isakmp)#authentication pre-share 
R27(config-isakmp)#group 2
R27(config-isakmp)#exit 
R27(config)#crypto isakmp key qwerty1234 address 0.0.0.0
R27(config)#crypto ipsec transform-set MSK esp-3des esp-md5-hmac 
R27(cfg-crypto-trans)#mode tunnel 
R27(cfg-crypto-trans)#exit
R27(config)#crypto ipsec profile MOSCOW
R27(ipsec-profile)#set security-association lifetime seconds 86400
R27(ipsec-profile)#set transform-set MSK
R27(ipsec-profile)#exit 
R27(config)#interface tunnel 100
R27(config-if)#tunnel protection ipsec profile MOSCOW
R27(config-if)#end
R27#wr
```
```
R15#show crypto isakmp sa 
IPv4 Crypto ISAKMP SA
dst             src             state          conn-id status
77.94.165.2     109.72.1.34     QM_IDLE           1008 ACTIVE
77.94.165.2     109.72.1.26     QM_IDLE           1007 ACTIVE

IPv6 Crypto ISAKMP SA


R15#show dmvpn
Legend: Attrb --> S - Static, D - Dynamic, I - Incomplete
        N - NATed, L - Local, X - No Socket
        # Ent --> Number of NHRP entries with same NBMA peer
        NHS Status: E --> Expecting Replies, R --> Responding, W --> Waiting
        UpDn Time --> Up or Down Time for a Tunnel
==========================================================================

Interface: Tunnel100, IPv4 NHRP Details 
Type:Hub, NHRP Peers:2, 

 # Ent  Peer NBMA Addr Peer Tunnel Add State  UpDn Tm Attrb
 ----- --------------- --------------- ----- -------- -----
     1 109.72.1.26          10.20.20.2    UP    3d01h     D
     1 109.72.1.34          10.20.20.3    UP    3d01h     D
```
**R28**

```
R28>en
R28#conf t
R28(config)#interface Tunnel100
R28(config-if)#ip address 10.20.20.3 255.255.255.0
R28(config-if)#no ip redirects
R28(config-if)#ip mtu 1440
R28(config-if)#ip nhrp authentication MSK
R28(config-if)#ip nhrp map multicast dynamic
R28(config-if)#ip nhrp map 10.20.20.1 77.94.165.2
R28(config-if)#ip nhrp map multicast 77.94.165.2
R28(config-if)#ip nhrp network-id 1
R28(config-if)#ip nhrp nhs 10.20.20.1
R28(config-if)#ip nhrp registration no-unique
R28(config-if)#load-interval 30
R28(config-if)#keepalive 5 10
R28(config-if)#tunnel source Ethernet0/0
R28(config-if)#tunnel mode gre multipoint
R28(config-if)#exit
R28(config)#crypto isakmp key qwerty1234 address 0.0.0.0
R28(config)#crypto ipsec transform-set MSK esp-3des esp-md5-hmac 
R28(cfg-crypto-trans)#mode tunnel 
R28(cfg-crypto-trans)#exit
R28(config)#crypto ipsec profile MOSCOW
R28(ipsec-profile)#set security-association lifetime seconds 86400
R28(ipsec-profile)#set transform-set MSK
R28(ipsec-profile)#exit 
R28(config)#interface tunnel 100
R28(config-if)#tunnel protection ipsec profile MOSCOW
R28(config-if)#end
R28#wr
```
```
R28#show crypto isakmp sa 
IPv4 Crypto ISAKMP SA
dst             src             state          conn-id status
77.94.165.2     109.72.1.34     QM_IDLE           1001 ACTIVE
109.72.1.26     109.72.1.34     QM_IDLE           1002 ACTIVE
109.72.1.34     109.72.1.26     QM_IDLE           1003 ACTIVE

IPv6 Crypto ISAKMP SA

R28#show dmvpn            
Legend: Attrb --> S - Static, D - Dynamic, I - Incomplete
        N - NATed, L - Local, X - No Socket
        # Ent --> Number of NHRP entries with same NBMA peer
        NHS Status: E --> Expecting Replies, R --> Responding, W --> Waiting
        UpDn Time --> Up or Down Time for a Tunnel
==========================================================================

Interface: Tunnel100, IPv4 NHRP Details 
Type:Spoke, NHRP Peers:2, 

 # Ent  Peer NBMA Addr Peer Tunnel Add State  UpDn Tm Attrb
 ----- --------------- --------------- ----- -------- -----
     2 77.94.165.2          10.20.20.1    UP    3d01h     S
                            10.20.20.3    UP 00:00:03     D
     1 109.72.1.26          10.20.20.2    UP 00:06:18     D
```

****Проверка****

**R15**

```
R15#ping 10.20.20.1
Type escape sequence to abort.
Sending 5, 100-byte ICMP Echos to 10.20.20.1, timeout is 2 seconds:
!!!!!
Success rate is 100 percent (5/5), round-trip min/avg/max = 4/4/5 ms
R15#ping 10.20.20.2
Type escape sequence to abort.
Sending 5, 100-byte ICMP Echos to 10.20.20.2, timeout is 2 seconds:
!!!!!
Success rate is 100 percent (5/5), round-trip min/avg/max = 6/6/7 ms
R15#ping 10.20.20.3
Type escape sequence to abort.
Sending 5, 100-byte ICMP Echos to 10.20.20.3, timeout is 2 seconds:
!!!!!
Success rate is 100 percent (5/5), round-trip min/avg/max = 6/6/7 ms
```

**R27**

```
R27#ping 10.20.20.1
Type escape sequence to abort.
Sending 5, 100-byte ICMP Echos to 10.20.20.1, timeout is 2 seconds:
!!!!!
Success rate is 100 percent (5/5), round-trip min/avg/max = 6/6/7 ms
R27#ping 10.20.20.2
Type escape sequence to abort.
Sending 5, 100-byte ICMP Echos to 10.20.20.2, timeout is 2 seconds:
!!!!!
Success rate is 100 percent (5/5), round-trip min/avg/max = 6/6/7 ms
R27#ping 10.20.20.3
Type escape sequence to abort.
Sending 5, 100-byte ICMP Echos to 10.20.20.3, timeout is 2 seconds:
!!!!!
Success rate is 100 percent (5/5), round-trip min/avg/max = 3/4/6 ms
```

**R28**

```
R28#ping 10.20.20.1
Type escape sequence to abort.
Sending 5, 100-byte ICMP Echos to 10.20.20.1, timeout is 2 seconds:
!!!!!
Success rate is 100 percent (5/5), round-trip min/avg/max = 5/5/6 ms
R28#ping 10.20.20.2
Type escape sequence to abort.
Sending 5, 100-byte ICMP Echos to 10.20.20.2, timeout is 2 seconds:
!!!!!
Success rate is 100 percent (5/5), round-trip min/avg/max = 5/5/6 ms
R28#ping 10.20.20.3
Type escape sequence to abort.
Sending 5, 100-byte ICMP Echos to 10.20.20.3, timeout is 2 seconds:
!!!!!
Success rate is 100 percent (5/5), round-trip min/avg/max = 6/7/8 ms
```
### Все узлы в офисах в лабораторной работе должны иметь IP связность.

```
R15#ping 109.72.1.38
Type escape sequence to abort.
Sending 5, 100-byte ICMP Echos to 109.72.1.38, timeout is 2 seconds:
!!!!!
Success rate is 100 percent (5/5), round-trip min/avg/max = 1/1/1 ms
R15#ping 109.72.1.42
Type escape sequence to abort.
Sending 5, 100-byte ICMP Echos to 109.72.1.42, timeout is 2 seconds:
!!!!!
Success rate is 100 percent (5/5), round-trip min/avg/max = 1/1/1 ms
R15#ping 109.72.1.34
Type escape sequence to abort.
Sending 5, 100-byte ICMP Echos to 109.72.1.34, timeout is 2 seconds:
!!!!!
Success rate is 100 percent (5/5), round-trip min/avg/max = 1/1/2 ms
R15#ping 109.72.1.30
Type escape sequence to abort.
Sending 5, 100-byte ICMP Echos to 109.72.1.30, timeout is 2 seconds:
!!!!!
Success rate is 100 percent (5/5), round-trip min/avg/max = 1/1/2 ms
R15#ping 109.72.1.26
Type escape sequence to abort.
Sending 5, 100-byte ICMP Echos to 109.72.1.26, timeout is 2 seconds:
!!!!!
Success rate is 100 percent (5/5), round-trip min/avg/max = 1/1/2 ms
```
