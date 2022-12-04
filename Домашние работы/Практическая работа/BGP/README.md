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
82.138.2.1      4          101      44      28       49    0    0 00:19:41        1
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
77.94.165.1     4          301     230     218       39    0    0 03:12:17        1
```

**R21**

```
R21>en
R21#conf t
R21(config)#router bgp 301
R21(config-router)#bgp router-id 21.21.21.21
R21(config-router)#network 77.94.165.0 mask 255.255.255.252
R21(config-router)#neighbor 77.94.165.2 remote-as 1001

R21#show ip bgp summary

Neighbor        V           AS MsgRcvd MsgSent   TblVer  InQ OutQ Up/Down  State/PfxRcd
77.94.165.2     4         1001     183     195       39    0    0 02:40:23        6
```

**R22**

```
R22>en
R22#conf t
R22(config)#router bgp 101
R22(config-router)#bgp router-id 22.22.22.22
R22(config-router)#network 82.138.2.0 mask 255.255.255.252
R22(config-router)#neighbor 82.138.2.2 remote-as 1001

R22#sh ip bgp summary

Neighbor        V           AS MsgRcvd MsgSent   TblVer  InQ OutQ Up/Down  State/PfxRcd
82.138.2.2      4         1001      27      43       30    0    0 00:18:36        6
```

### ***2) Настроите eBGP между провайдерами Киторн и Ламас*** 


