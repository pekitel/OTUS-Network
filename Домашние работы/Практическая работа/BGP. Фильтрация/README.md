# Задание
1. Настроить фильтрацию в офисе Москва так, чтобы не появилось транзитного трафика(As-path).
2. Настроить фильтрацию в офисе С.-Петербург так, чтобы не появилось транзитного трафика(Prefix-list).
3. Настроить провайдера Киторн так, чтобы в офис Москва отдавался только маршрут по умолчанию.
4. Настроить провайдера Ламас так, чтобы в офис Москва отдавался только маршрут по умолчанию и префикс офиса С.-Петербург.
5. Все сети в лабораторной работе должны иметь IP связность.

## Карта сети ipv4

![BGP](https://user-images.githubusercontent.com/112701413/207262186-a96153d0-f3eb-4392-84e5-7abff1d7ea61.jpg)


## Карта сети ipv6

![BGP-ipv6](https://user-images.githubusercontent.com/112701413/207262240-9314e3f8-23b7-4186-a807-d1b44be9190c.jpg)

### ***Настроить фильтрацию в офисе Москва так, чтобы не появилось транзитного трафика(As-path)***

**R14**
```
R14>en
R14#conf t
R14(config)#ip as-path access-list 1 permit ^$
R14(config)#ip as-path access-list 1 deny .*
R14(config)#router bgp 1001
R14(config-router)#address-family ipv4 unicast
R14(config-router-af)#neighbor 82.138.2.1 filter-list 1 out
R14(config-router-af)#exit-address-family
R14(config-router)#address-family ipv6 unicast
R14(config-router-af)#neighbor 2000:ABCD:EEBB:FFFF:1::1 filter-list 1 out
R14(config-router-af)#end
R14#wr
```
**R15**
```
R15>en
R15#conf t
R15(config)#ip as-path access-list 1 permit ^$
R15(config)#ip as-path access-list 1 deny .*
R15(config)#router bgp 1001
R15(config-router)#address-family ipv4 unicast
R15(config-router-af)#neighbor 77.94.165.1 filter-list 1 out
R15(config-router-af)#exit-address-family
R15(config-router)#address-family ipv6 unicast
R15(config-router-af)#neighbor 1999:ABCD:EEBB:FFFF:1::1 filter-list 1 out
R15(config-router-af)#end
R15#wr
```
***Проверим провайдерские роутеры на наличие маршрутов***
**R22**
```
R22#sh ip bgp
BGP table version is 21, local router ID is 22.22.22.22
Status codes: s suppressed, d damped, h history, * valid, > best, i - internal,
              r RIB-failure, S Stale, m multipath, b backup-path, f RT-Filter,
              x best-external, a additional-path, c RIB-compressed,
Origin codes: i - IGP, e - EGP, ? - incomplete
RPKI validation codes: V valid, I invalid, N Not found

     Network          Next Hop            Metric LocPrf Weight Path
 *   77.37.144.252/30 82.138.2.6                             0 301 1001 i
 *>                   82.138.2.2               0             0 1001 i
 *>  77.94.165.0/30   82.138.2.2                             0 1001 i
 *                    82.138.2.6                             0 301 1001 i
 r   82.138.2.0/30    82.138.2.6                             0 301 1001 i
 r>                   82.138.2.2               0             0 1001 i
 *   109.72.1.36/30   82.138.2.6                             0 301 520 2042 i
 *>                   109.72.1.17                            0 520 2042 i
 *   109.72.1.40/30   82.138.2.6                             0 301 520 2042 i
 *>                   109.72.1.17                            0 520 2042 i
 *   109.72.67.28/32  82.138.2.6                             0 301 520 ?
 *>                   109.72.1.17                            0 520 ?
 *   109.72.68.27/32  82.138.2.6                             0 301 520 ?
 *>                   109.72.1.17                            0 520 ?

Видим что АС 1001 анонсирует только свои сети и не является транзитом для других
```
**R21**
```
R21#show ip bgp
BGP table version is 25, local router ID is 21.21.21.21
Status codes: s suppressed, d damped, h history, * valid, > best, i - internal,
              r RIB-failure, S Stale, m multipath, b backup-path, f RT-Filter,
              x best-external, a additional-path, c RIB-compressed,
Origin codes: i - IGP, e - EGP, ? - incomplete
RPKI validation codes: V valid, I invalid, N Not found

     Network          Next Hop            Metric LocPrf Weight Path
 *>  77.37.144.252/30 77.94.165.2              0             0 1001 i
 *                    82.138.2.5                             0 101 1001 i
 r   77.94.165.0/30   82.138.2.5                             0 101 1001 i
 r>                   77.94.165.2              0             0 1001 i
 *>  82.138.2.0/30    77.94.165.2                            0 1001 i
 *                    82.138.2.5                             0 101 1001 i
 *>  109.72.1.36/30   109.72.1.21                            0 520 2042 i
 *                    82.138.2.5                             0 101 520 2042 i
 *>  109.72.1.40/30   109.72.1.21                            0 520 2042 i
 *                    82.138.2.5                             0 101 520 2042 i
 *   109.72.67.28/32  82.138.2.5                             0 101 520 ?
 *>                   109.72.1.21                            0 520 ?
 *   109.72.68.27/32  82.138.2.5                             0 101 520 ?
 *>                   109.72.1.21                            0 520 ?
Видим аналогичную ситуация
```

### Настроить фильтрацию в офисе С.-Петербург так, чтобы не появилось транзитного трафика(Prefix-list)
