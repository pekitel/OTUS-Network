# Задание

1. [Настроить GRE между офисами Москва и С.-Петербург](https://github.com/pekitel/OTUS-Network/blob/main/%D0%94%D0%BE%D0%BC%D0%B0%D1%88%D0%BD%D0%B8%D0%B5%20%D1%80%D0%B0%D0%B1%D0%BE%D1%82%D1%8B/%D0%9F%D1%80%D0%B0%D0%BA%D1%82%D0%B8%D1%87%D0%B5%D1%81%D0%BA%D0%B0%D1%8F%20%D1%80%D0%B0%D0%B1%D0%BE%D1%82%D0%B0/%D0%92%D0%B8%D1%80%D1%82%D1%83%D0%B0%D0%BB%D1%8C%D0%BD%D0%B0%D1%8F%20%D1%87%D0%B0%D1%81%D1%82%D0%BD%D1%8B%D0%B5%20%D1%81%D0%B5%D1%82%D0%B8%20-%20VPN/README.md#%D0%BD%D0%B0%D1%81%D1%82%D1%80%D0%BE%D0%B8%D1%82%D1%8C-gre-%D0%BC%D0%B5%D0%B6%D0%B4%D1%83-%D0%BE%D1%84%D0%B8%D1%81%D0%B0%D0%BC%D0%B8-%D0%BC%D0%BE%D1%81%D0%BA%D0%B2%D0%B0-%D0%B8-%D1%81-%D0%BF%D0%B5%D1%82%D0%B5%D1%80%D0%B1%D1%83%D1%80%D0%B3)
2. [Настроить DMVPN между офисами Москва и Чокурдах, Лабытнанги](https://github.com/pekitel/OTUS-Network/blob/main/%D0%94%D0%BE%D0%BC%D0%B0%D1%88%D0%BD%D0%B8%D0%B5%20%D1%80%D0%B0%D0%B1%D0%BE%D1%82%D1%8B/%D0%9F%D1%80%D0%B0%D0%BA%D1%82%D0%B8%D1%87%D0%B5%D1%81%D0%BA%D0%B0%D1%8F%20%D1%80%D0%B0%D0%B1%D0%BE%D1%82%D0%B0/%D0%92%D0%B8%D1%80%D1%82%D1%83%D0%B0%D0%BB%D1%8C%D0%BD%D0%B0%D1%8F%20%D1%87%D0%B0%D1%81%D1%82%D0%BD%D1%8B%D0%B5%20%D1%81%D0%B5%D1%82%D0%B8%20-%20VPN/README.md#%D0%BD%D0%B0%D1%81%D1%82%D1%80%D0%BE%D0%B8%D1%82%D1%8C-dmvpn-%D0%BC%D0%B5%D0%B6%D0%B4%D1%83-%D0%BE%D1%84%D0%B8%D1%81%D0%B0%D0%BC%D0%B8-%D0%BC%D0%BE%D1%81%D0%BA%D0%B2%D0%B0-%D0%B8-%D1%87%D0%BE%D0%BA%D1%83%D1%80%D0%B4%D0%B0%D1%85-%D0%BB%D0%B0%D0%B1%D1%8B%D1%82%D0%BD%D0%B0%D0%BD%D0%B3%D0%B8)

## Карта сети

![карта_new](https://user-images.githubusercontent.com/112701413/215794845-219d28ee-0306-4549-ae75-3bd5d0f0d210.jpg)


### Настроить GRE между офисами Москва и С.-Петербург

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
R14#wr
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
R18#wr
```
### ***Проверка***

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
Success rate is 100 percent (5/5), round-trip min/avg/max = 1/1/2 ms
```

### Настроить DMVPN между офисами Москва и Чокурдах, Лабытнанги

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
R15(config)#exit
R15#wr
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
R27(config)#exit
R27#wr
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
R28(config)#exit
R28#wr
```

### ***Проверка***

**R15**

```
R15#show dmvpn  
Legend: Attrb --> S - Static, D - Dynamic, I - Incomplete
        N - NATed, L - Local, X - No Socket
        # Ent --> Number of NHRP entries with same NBMA peer
        NHS Status: E --> Expecting Replies, R --> Responding, W --> Waiting
        UpDn Time --> Up or Down Time for a Tunnel
==========================================================================

Interface: Tunnel100, IPv4 NHRP Details 
Type:Hub, NHRP Peers:3, 

 # Ent  Peer NBMA Addr Peer Tunnel Add State  UpDn Tm Attrb
 ----- --------------- --------------- ----- -------- -----
     1 UNKNOWN              10.20.20.1  NHRP    never    IX
     1 109.72.1.26          10.20.20.2    UP 00:01:43     D
     1 109.72.1.34          10.20.20.3    UP 00:09:21     D
```
 
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
Success rate is 100 percent (5/5), round-trip min/avg/max = 1/1/2 ms
R15#ping 10.20.20.3
Type escape sequence to abort.
Sending 5, 100-byte ICMP Echos to 10.20.20.3, timeout is 2 seconds:
!!!!!
Success rate is 100 percent (5/5), round-trip min/avg/max = 1/1/2 ms
```

**R28**

```
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
     1 77.94.165.2          10.20.20.1    UP 00:09:00     S
     1 109.72.1.26          10.20.20.2    UP 00:00:03     D
```

```
R28#ping 10.20.20.1
Type escape sequence to abort.
Sending 5, 100-byte ICMP Echos to 10.20.20.1, timeout is 2 seconds:
!!!!!
Success rate is 100 percent (5/5), round-trip min/avg/max = 1/1/3 ms
R28#ping 10.20.20.2
Type escape sequence to abort.
Sending 5, 100-byte ICMP Echos to 10.20.20.2, timeout is 2 seconds:
!!!!!
Success rate is 100 percent (5/5), round-trip min/avg/max = 1/1/1 ms
R28#ping 10.20.20.3
Type escape sequence to abort.
Sending 5, 100-byte ICMP Echos to 10.20.20.3, timeout is 2 seconds:
!!!!!
Success rate is 100 percent (5/5), round-trip min/avg/max = 1/1/2 ms
```

**R27**

```
R27#sh dmvpn 
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
     1 77.94.165.2          10.20.20.1    UP 00:04:03     S
     1 109.72.1.34          10.20.20.3    UP 00:02:53     D
```

```
R27#ping 10.20.20.1
Type escape sequence to abort.
Sending 5, 100-byte ICMP Echos to 10.20.20.1, timeout is 2 seconds:
!!!!!
Success rate is 100 percent (5/5), round-trip min/avg/max = 1/2/3 ms
R27#ping 10.20.20.2
Type escape sequence to abort.
Sending 5, 100-byte ICMP Echos to 10.20.20.2, timeout is 2 seconds:
!!!!!
Success rate is 100 percent (5/5), round-trip min/avg/max = 2/2/4 ms
R27#ping 10.20.20.3
Type escape sequence to abort.
Sending 5, 100-byte ICMP Echos to 10.20.20.3, timeout is 2 seconds:
!!!!!
Success rate is 100 percent (5/5), round-trip min/avg/max = 1/1/2 ms
```
