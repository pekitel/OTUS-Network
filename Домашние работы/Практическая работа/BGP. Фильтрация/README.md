# Задание
1. [Настроить фильтрацию в офисе Москва так, чтобы не появилось транзитного трафика(As-path).](https://github.com/pekitel/OTUS-Network/blob/main/%D0%94%D0%BE%D0%BC%D0%B0%D1%88%D0%BD%D0%B8%D0%B5%20%D1%80%D0%B0%D0%B1%D0%BE%D1%82%D1%8B/%D0%9F%D1%80%D0%B0%D0%BA%D1%82%D0%B8%D1%87%D0%B5%D1%81%D0%BA%D0%B0%D1%8F%20%D1%80%D0%B0%D0%B1%D0%BE%D1%82%D0%B0/BGP.%20%D0%A4%D0%B8%D0%BB%D1%8C%D1%82%D1%80%D0%B0%D1%86%D0%B8%D1%8F/README.md#%D0%BD%D0%B0%D1%81%D1%82%D1%80%D0%BE%D0%B8%D1%82%D1%8C-%D1%84%D0%B8%D0%BB%D1%8C%D1%82%D1%80%D0%B0%D1%86%D0%B8%D1%8E-%D0%B2-%D0%BE%D1%84%D0%B8%D1%81%D0%B5-%D0%BC%D0%BE%D1%81%D0%BA%D0%B2%D0%B0-%D1%82%D0%B0%D0%BA-%D1%87%D1%82%D0%BE%D0%B1%D1%8B-%D0%BD%D0%B5-%D0%BF%D0%BE%D1%8F%D0%B2%D0%B8%D0%BB%D0%BE%D1%81%D1%8C-%D1%82%D1%80%D0%B0%D0%BD%D0%B7%D0%B8%D1%82%D0%BD%D0%BE%D0%B3%D0%BE-%D1%82%D1%80%D0%B0%D1%84%D0%B8%D0%BA%D0%B0as-path)
2. [Настроить фильтрацию в офисе С.-Петербург так, чтобы не появилось транзитного трафика(Prefix-list).](https://github.com/pekitel/OTUS-Network/blob/main/%D0%94%D0%BE%D0%BC%D0%B0%D1%88%D0%BD%D0%B8%D0%B5%20%D1%80%D0%B0%D0%B1%D0%BE%D1%82%D1%8B/%D0%9F%D1%80%D0%B0%D0%BA%D1%82%D0%B8%D1%87%D0%B5%D1%81%D0%BA%D0%B0%D1%8F%20%D1%80%D0%B0%D0%B1%D0%BE%D1%82%D0%B0/BGP.%20%D0%A4%D0%B8%D0%BB%D1%8C%D1%82%D1%80%D0%B0%D1%86%D0%B8%D1%8F/README.md#%D0%BD%D0%B0%D1%81%D1%82%D1%80%D0%BE%D0%B8%D1%82%D1%8C-%D1%84%D0%B8%D0%BB%D1%8C%D1%82%D1%80%D0%B0%D1%86%D0%B8%D1%8E-%D0%B2-%D0%BE%D1%84%D0%B8%D1%81%D0%B5-%D1%81-%D0%BF%D0%B5%D1%82%D0%B5%D1%80%D0%B1%D1%83%D1%80%D0%B3-%D1%82%D0%B0%D0%BA-%D1%87%D1%82%D0%BE%D0%B1%D1%8B-%D0%BD%D0%B5-%D0%BF%D0%BE%D1%8F%D0%B2%D0%B8%D0%BB%D0%BE%D1%81%D1%8C-%D1%82%D1%80%D0%B0%D0%BD%D0%B7%D0%B8%D1%82%D0%BD%D0%BE%D0%B3%D0%BE-%D1%82%D1%80%D0%B0%D1%84%D0%B8%D0%BA%D0%B0prefix-list)
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

**R18**
```
interface Loopback18
ip address 33.72.66.18 255.255.255.255
ipv6 address 2003:ABCD:EEBB:BBBB::18/128
Наша сети
--------------------------------------------------------------------------------------------
R18>en
R18#conf t
R18(config)#ip as-path access-list 1 permit ^$
R18(config)#ip as-path access-list 1 deny .*
R18(config)#ip prefix-list Default seq 15 permit 33.72.66.0/24 le 32
R18(config)#ip prefix-list Default seq 20 deny 0.0.0.0/0 le 32
R18(config)#ipv6 prefix-list Default-ipv6 seq 25 permit 2003:ABCD:EEBB:BBBB::/64 le 128
R18(config)#ipv6 prefix-list Default-ipv6 seq 30 deny ::/0 le 32
R18(config)#route-map Filter permit 10
R18(config-route-map)#match ip address prefix-list Default
R18(config-route-map)#exit
R18(config)#route-map Filter permit 15
R18(config-route-map)#match ipv6 address prefix-list Default-ipv6
R18(config-route-map)#exit
R18(config)#router bgp 2042
R18(config-router)#template peer-policy TRIADA_POLICY_ipv6
R18(config-router-ptmp)#route-map Filter_ipv6 out
R18(config-router-ptmp)#filter-list 1 out
R18(config-router-ptmp)#exit
R18(config-router)#template peer-policy TRIADA_POLICY
R18(config-router-ptmp)#route-map Filter out
R18(config-router-ptmp)#filter-list 1 out
R18(config-router-ptmp)#exit
R18(config-router)#template peer-session TRIADA_ipv6
R18(config-router-stmp)#remote-as 520
R18(config-router-stmp)#exit-peer-session
R18(config-router)#template peer-session TRIADA
R18(config-router-stmp)#remote-as 520
R18(config-router-stmp)#exit-peer-session
R18(config-router)#neighbor 109.72.1.37 inherit peer-session TRIADA
R18(config-router)#neighbor 109.72.1.41 inherit peer-session TRIADA
R18(config-router)#neighbor 2002:ABCD:EEBB:FFFF:A::1 inherit peer-session TRIADA_ipv6
R18(config-router)#neighbor 2002:ABCD:EEBB:FFFF:B::1 inherit peer-session TRIADA_ipv6
R18(config-router)#address-family ipv4 unicast
R18(config-router-af)#neighbor 109.72.1.37 inherit peer-policy TRIADA_POLICY
R18(config-router-af)#neighbor 109.72.1.41 inherit peer-policy TRIADA_POLICY
R18(config-router-af)#exit-address-family
R18(config-router)#address-family ipv6 unicast
R18(config-router-af)#neighbor 2002:ABCD:EEBB:FFFF:A::1 inherit peer-policy TRIADA_POLICY_ipv6
R18(config-router-af)#neighbor 2002:ABCD:EEBB:FFFF:B::1 inherit peer-policy TRIADA_POLICY_ipv6
R18(config-router-af)#end
R18#wr
```
***Теперь посмотрим,что приходит у провайдера Триада (R24/R26)***

**R24**
```
R24#show ip bgp ipv4 unicast
BGP table version is 49, local router ID is 24.24.24.24
Status codes: s suppressed, d damped, h history, * valid, > best, i - internal,
              r RIB-failure, S Stale, m multipath, b backup-path, f RT-Filter,
              x best-external, a additional-path, c RIB-compressed,
Origin codes: i - IGP, e - EGP, ? - incomplete
RPKI validation codes: V valid, I invalid, N Not found

     Network          Next Hop            Metric LocPrf Weight Path
 * i 33.72.66.0/24    109.72.255.26      1024640    100      0 2042 i
 *>                   109.72.1.38        1024640             0 2042 i
 *>  77.37.144.252/30 109.72.1.22                            0 301 1001 i
 * i                  109.72.255.23            0    100      0 101 1001 i
 * i 77.94.165.0/30   109.72.255.23            0    100      0 101 1001 i
 *>                   109.72.1.22                            0 301 1001 i
 *>  82.138.2.0/30    109.72.1.22                            0 301 1001 i
 * i                  109.72.255.23            0    100      0 101 1001 i
 *>i 109.72.67.28/32  109.72.255.26            0    100      0 ?
 * i                  109.72.255.25            0    100      0 ?
 *>i 109.72.68.27/32  109.72.255.25            0    100      0 ?
--------------------------------------------------------------------------------------
Нас лишь интересует маршрут 33.72.66.0/24 за АС 2042
```
```
R24#show ip bgp ipv6 unicast
BGP table version is 45, local router ID is 24.24.24.24
Status codes: s suppressed, d damped, h history, * valid, > best, i - internal,
              r RIB-failure, S Stale, m multipath, b backup-path, f RT-Filter,
              x best-external, a additional-path, c RIB-compressed,
Origin codes: i - IGP, e - EGP, ? - incomplete
RPKI validation codes: V valid, I invalid, N Not found

     Network          Next Hop            Metric LocPrf Weight Path
 * i 1999:ABCD:EEBB:FFFF:1::/80
                       2002:ABCD:EEBB:CCCC::23
                                                0    100      0 101 1001 i
 *>                   2002:ABCD:EEBB:FFFF:9::2
                                                              0 301 1001 i
 *>  2000:ABCD:EEBB:FFFF:1::/80
                       2002:ABCD:EEBB:FFFF:9::2
                                                              0 301 1001 i
 * i                  2002:ABCD:EEBB:CCCC::23
                                                0    100      0 101 1001 i
 *>  2001:ABCD:EEBB:AAAA:7::/80
                       2002:ABCD:EEBB:FFFF:9::2
                                                              0 301 1001 i
 * i                  2002:ABCD:EEBB:CCCC::23
     Network          Next Hop            Metric LocPrf Weight Path
                                                0    100      0 101 1001 i
 * i 2002:ABCD:EEBB:AAAA::28/128
                       2002:ABCD:EEBB:CCCC::25
                                                0    100      0 ?
 *>i                  2002:ABCD:EEBB:CCCC::26
                                                0    100      0 ?
 *>i 2002:ABCD:EEBB:BBBB::27/128
                       2002:ABCD:EEBB:CCCC::25
                                                0    100      0 ?
 * i 2003:ABCD:EEBB:BBBB::/64
                       2002:ABCD:EEBB:CCCC::26
                                          1024640    100      0 2042 i
 *>                   2002:ABCD:EEBB:FFFF:A::2
                                          1024640             0 2042 i
----------------------------------------------------------------------------------------
Нас лишь интересует маршрут 2003:ABCD:EEBB:BBBB::/64 за АС 2042
```
**R26**
```
R26#show ip bgp ipv4 unicast
BGP table version is 132, local router ID is 26.26.26.26
Status codes: s suppressed, d damped, h history, * valid, > best, i - internal,
              r RIB-failure, S Stale, m multipath, b backup-path, f RT-Filter,
              x best-external, a additional-path, c RIB-compressed,
Origin codes: i - IGP, e - EGP, ? - incomplete
RPKI validation codes: V valid, I invalid, N Not found

     Network          Next Hop            Metric LocPrf Weight Path
 * i 33.72.66.0/24    109.72.255.24      1024640    100      0 2042 i
 *>                   109.72.1.42        1024640             0 2042 i
 *>i 77.37.144.252/30 109.72.255.24            0    100      0 301 1001 i
 *>i 77.94.165.0/30   109.72.255.24            0    100      0 301 1001 i
 *>i 82.138.2.0/30    109.72.255.24            0    100      0 301 1001 i
 *>  109.72.67.28/32  109.72.1.34              0         32768 ?
 *>i 109.72.68.27/32  109.72.255.25            0    100      0 ?
--------------------------------------------------------------------------------------------
Нас лишь интересует маршрут 33.72.66.0/24 за АС 2042
```
```
R26#show ip bgp ipv6 unicast
BGP table version is 114, local router ID is 26.26.26.26
Status codes: s suppressed, d damped, h history, * valid, > best, i - internal,
              r RIB-failure, S Stale, m multipath, b backup-path, f RT-Filter,
              x best-external, a additional-path, c RIB-compressed,
Origin codes: i - IGP, e - EGP, ? - incomplete
RPKI validation codes: V valid, I invalid, N Not found

     Network          Next Hop            Metric LocPrf Weight Path
 *>i 1999:ABCD:EEBB:FFFF:1::/80
                       2002:ABCD:EEBB:CCCC::24
                                                0    100      0 301 1001 i
 *>i 2000:ABCD:EEBB:FFFF:1::/80
                       2002:ABCD:EEBB:CCCC::24
                                                0    100      0 301 1001 i
 *>i 2001:ABCD:EEBB:AAAA:7::/80
                       2002:ABCD:EEBB:CCCC::24
                                                0    100      0 301 1001 i
 *>  2002:ABCD:EEBB:AAAA::28/128
                       2002:ABCD:EEBB:FFFF:4::2
                                                0         32768 ?
 *>i 2002:ABCD:EEBB:BBBB::27/128
                       2002:ABCD:EEBB:CCCC::25
     Network          Next Hop            Metric LocPrf Weight Path
                                                0    100      0 ?
 * i 2003:ABCD:EEBB:BBBB::/64
                       2002:ABCD:EEBB:CCCC::24
                                          1024640    100      0 2042 i
 *>                   2002:ABCD:EEBB:FFFF:B::2
                                          1024640             0 2042 i
------------------------------------------------------------------------------------------------
Нас лишь интересует маршрут 2003:ABCD:EEBB:BBBB::/64 за АС 2042
```

### Настроить провайдера Киторн так, чтобы в офис Москва отдавался только маршрут по умолчанию

