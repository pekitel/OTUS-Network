# Задание

### Настроите eBGP между офисом Москва и двумя провайдерами - Киторн и Ламас.
### Настроите eBGP между провайдерами Киторн и Ламас.
### Настроите eBGP между Ламас и Триада.
### Настроите eBGP между офисом С.-Петербург и провайдером Триада.
### Организуете IP доступность между пограничным роутерами офисами Москва и С.-Петербург.

## Карта сети

![eBGP](https://user-images.githubusercontent.com/112701413/205439534-ae532414-9a12-4c0b-8c62-d4ee2009c3b8.jpg)

### ***1) Настроите eBGP между офисом Москва и двумя провайдерами - Киторн и Ламас*** 

**R14**

```
R14>en
R14#conf t
R14(config)#router bgp 1001
R14(config-router)#bgp router-id 14.14.14.14
R14(config-router)#network 77.37.144.12 mask 255.255.255.255
R14(config-router)#network 77.37.144.13 mask 255.255.255.255
R14(config-router)#network 77.37.144.14 mask 255.255.255.255
R14(config-router)#network 77.37.144.15 mask 255.255.255.255
R14(config-router)#network 77.37.144.19 mask 255.255.255.255
R14(config-router)#network 77.37.144.20 mask 255.255.255.255
R14(config-router)#network 82.138.2.0 mask 255.255.255.252
R14(config-router)#neighbor 82.138.2.1 remote-as 101
R14(config-router)#end
R14#show ip bgp summary

Neighbor        V           AS MsgRcvd MsgSent   TblVer  InQ OutQ Up/Down  State/PfxRcd
82.138.2.1      4          101      68      63       13    0    0 00:51:53        6
```

**R15**

```
R15>en
R15#conf t
R15(config)#router bgp 1001
R15(config-router)#bgp router-id 15.15.15.15
R15(config-router)#network 77.37.144.12 mask 255.255.255.255
R15(config-router)#network 77.37.144.13 mask 255.255.255.255
R15(config-router)#network 77.37.144.14 mask 255.255.255.255
R15(config-router)#network 77.37.144.15 mask 255.255.255.255
R15(config-router)#network 77.37.144.19 mask 255.255.255.255
R15(config-router)#network 77.37.144.20 mask 255.255.255.255
R15(config-router)#network 77.94.165.0 mask 255.255.255.252
R15(config-router)#neighbor 77.94.165.1 remote-as 301

R15#show ip bgp summary

Neighbor        V           AS MsgRcvd MsgSent   TblVer  InQ OutQ Up/Down  State/PfxRcd
77.94.165.1     4          301      67      63       12    0    0 00:52:28        6
```

**R21**

```
R21>en
R21#conf t
R21(config)#router bgp 301
R21(config-router)#bgp router-id 21.21.21.21
R21(config-router)#network 77.94.165.0 mask 255.255.255.252
R21(config-router)#neighbor 77.94.165.2 remote-as 1001
R21(config-router)#network 82.138.2.4 mask 255.255.255.252
R21(config-router)#neighbor 82.138.2.5 remote-as 101
R21(config-router)#network 109.72.1.20 mask 255.255.255.252
R21(config-router)#neighbor 109.72.1.21 remote-as 520

R21#show ip bgp summary

Neighbor        V           AS MsgRcvd MsgSent   TblVer  InQ OutQ Up/Down  State/PfxRcd
77.94.165.2     4         1001      73      79       17    0    0 01:01:55        6
82.138.2.5      4          101      18      22       17    0    0 00:07:39       10
109.72.1.21     4          520      78      79       17    0    0 01:01:56        4
```

**R22**

```
R22>en
R22#conf t
R22(config)#router bgp 101
R22(config-router)#bgp router-id 22.22.22.22
R22(config-router)#network 82.138.2.0 mask 255.255.255.252
R22(config-router)#neighbor 82.138.2.2 remote-as 1001
R22(config-router)#network 82.138.2.4 mask 255.255.255.252
R22(config-router)#neighbor 82.138.2.6 remote-as 301
R22(config-router)#network 109.72.1.16 mask 255.255.255.252
R22(config-router)#neighbor 109.72.1.17 remote-as 520

R22#sh ip bgp summary

Neighbor        V           AS MsgRcvd MsgSent   TblVer  InQ OutQ Up/Down  State/PfxRcd
82.138.2.2      4         1001       9      12       15    0    0 00:02:30        6
82.138.2.6      4          301      15      12       15    0    0 00:02:30       10
109.72.1.17     4          520      11      12       15    0    0 00:02:30        4
```

### ***2) Настроите eBGP между провайдерами Киторн и Ламас*** 
### ***3) Настроите eBGP между Ламас и Триада*** 


