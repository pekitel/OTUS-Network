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
