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
R14(config-router)#neighbor 10.10.1.26 remote-as 1001
R14(config-router)#neighbor 82.138.2.1 remote-as 101

R14#show ip bgp summary

Neighbor        V           AS MsgRcvd MsgSent   TblVer  InQ OutQ Up/Down  State/PfxRcd
10.10.1.26      4         1001    1397    1407       74    0    0 20:53:26       18
82.138.2.1      4          101    1434    1434       74    0    0 21:22:39       15

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
R15(config-router)#neighbor 10.10.1.25 remote-as 1001
R15(config-router)#neighbor 77.94.165.1 remote-as 301

R15#sh ip bgp summary

Neighbor        V           AS MsgRcvd MsgSent   TblVer  InQ OutQ Up/Down  State/PfxRcd
10.10.1.25      4         1001    1416    1406       53    0    0 21:01:32       18
77.94.165.1     4          301    1409    1400       53    0    0 21:04:17       15

```

**R21**

```
R21>en
R21#conf t
R21(config)#router bgp 301
R21(config-router)#bgp router-id 21.21.21.21
R21(config-router)#network 77.94.165.0 mask 255.255.255.252
R21(config-router)#network 82.138.2.4 mask 255.255.255.252
R21(config-router)#network 109.72.1.20 mask 255.255.255.252
R21(config-router)#neighbor 77.94.165.2 remote-as 1001
R21(config-router)#neighbor 82.138.2.5 remote-as 101
R21(config-router)#neighbor 109.72.1.21 remote-as 520

R21#show ip bgp summary

Neighbor        V           AS MsgRcvd MsgSent   TblVer  InQ OutQ Up/Down  State/PfxRcd
77.94.165.2     4         1001    1408    1417      120    0    0 21:10:52        9
82.138.2.5      4          101    1452    1449      120    0    0 21:43:46       19
109.72.1.21     4          520    1452    1455      120    0    0 21:42:22       12
```
