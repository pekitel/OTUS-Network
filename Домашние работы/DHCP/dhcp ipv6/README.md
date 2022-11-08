# DHCP ipv6


#### Настройка [R1](https://github.com/pekitel/OTUS-Network/blob/main/%D0%94%D0%BE%D0%BC%D0%B0%D1%88%D0%BD%D0%B8%D0%B5%20%D1%80%D0%B0%D0%B1%D0%BE%D1%82%D1%8B/DHCP/dhcp%20ipv6/README.md#%D0%BD%D0%B0%D1%81%D1%82%D1%80%D0%BE%D0%B9%D0%BA%D0%B0-r1-1)
#### Настройка [R2](https://github.com/pekitel/OTUS-Network/blob/main/%D0%94%D0%BE%D0%BC%D0%B0%D1%88%D0%BD%D0%B8%D0%B5%20%D1%80%D0%B0%D0%B1%D0%BE%D1%82%D1%8B/DHCP/dhcp%20ipv6/README.md#%D0%BD%D0%B0%D1%81%D1%82%D1%80%D0%BE%D0%B9%D0%BA%D0%B0-r2-c-%D0%BE%D1%82%D1%81%D0%BB%D0%B5%D0%B6%D0%B8%D0%B2%D0%B0%D0%BD%D0%B8%D1%8F-%D1%81%D0%BE%D1%81%D1%82%D0%BE%D1%8F%D0%BD%D0%B8%D1%8F-%D0%B8-relay)

## Схема сети

![ipv6](https://user-images.githubusercontent.com/112701413/193928748-a9eab94c-1479-4985-905b-4e1732a61fce.jpg)


  ## ipv6 address 
host | int | ip address |
:----:  | :----------: | :----: | 
R1 | e0/0 |2001:db8:acad:2::1/64 |
| |  |fe80::1 |
| | e0/1 | 2001:db8:acad:1::1/64 |
| |  |fe80::1 |
R2 | e0/0 | 2001:db8:acad:2::2/64 |
| |  |fe80::2 |
| | e0/1 | 2001:db8:acad:3::1/64 |
| |  |fe80::1 |
PC1 | eth0 | dhcp |
PC2 | eth0 | dhcp |

## Настройка R1 без отслеживания состояния
1. Заходим в превилегированый режим **enable**
2. Переходим в режим конфигурации устройства **configure terminal**
3. Задаём имя для роутера **hostname R1**
>![1](https://user-images.githubusercontent.com/112701413/194334686-025df8c6-a8ea-43d3-ba4b-909d7d871875.jpg)
4. Перейдем в интерфейс e0/0 **interface eth 0/0**
5. Зададем ipv6 адрес **ipv6 address 2001:db8:acad:2::1/64**
6. Зададим ipv6 *link-local* адрес **ipv6 address fe80::1 link-local**
7. Включим интерфейс **no shutdown**
>![2](https://user-images.githubusercontent.com/112701413/194485974-970f3414-29b9-4f05-83e3-41c9cf835b1a.jpg)
8. Перейдем в интерфейс e0/1 **interface eth 0/1**
9. Зададем ipv6 адрес **ipv6 address 2001:db8:acad:1::1/64**
10. Зададим ipv6 *link-local* адрес **ipv6 address fe80::1 link-local**
11. Включим интерфейс **no shutdown**
>![4](https://user-images.githubusercontent.com/112701413/194757899-550ca17f-1591-41ac-b870-a64f057aff8a.jpg)
12. Включим роутинг ipv6 **ipv6 unicast-routing**
>![5](https://user-images.githubusercontent.com/112701413/194757985-0507561d-3c64-46b7-a9c0-c5544f6eef75.jpg)
13. Проверим получает ли PC1 ipv6 адрес через SLAAC
14. На PC1 введём команду **ip auto**
15. Посмотри настройки интерфейса **show ipv6**
>![3](https://user-images.githubusercontent.com/112701413/194756191-afb6a6d1-c9a8-476a-bd30-ec022da1d146.jpg)
16. Настроим DHCPv6 на R1 без отслеживания состояния **ipv6 dhcp pool IPV6**
17. Назначим пулу имя домена **domain-name lab3.ru**
18. Назначим адрес сервера DNS **dns-server 2a02:6b8::feed:0ff**
19. Перейдем к интерфейсу e0/1 **int e0/1**
20. Назначим пул DHCPv6 интерфейсу e0/1 **ipv6 dhcp server IPV6**  
21. Установим флаг *other* **ipv6 nd other-config-flag**
>![7](https://user-images.githubusercontent.com/112701413/194761432-b242b69a-38f4-4eee-bb74-29ab34b7b333.jpg)
22. Проверим настройки DHCPv6 на интерфейсе e0/1 **show ipv6 int e0/1**
>![6](https://user-images.githubusercontent.com/112701413/194761443-48f8d76c-f0f8-4baa-8aa6-1460fcc2c67f.jpg)
23. Проверим получил ли PC1 адрес из пула **show ipv6 dhcp binding** и **show ipv6 dhcp pool**
>![8](https://user-images.githubusercontent.com/112701413/194761984-67c16ca2-ac02-4c81-b2a3-58d4787ffcfe.jpg)
24. Видим что PC1 не получил адрес из пула т.к. нет отслеживания состояния
25. Настроим ещё один DHCPv6 сервер для R2 **ipv6 dhcp pool IPV6-2**
26. Назначим пулу имя домена **domain-name lab3-2.ru**
27. Назначим адрес сервера DNS **dns-server 2001:DB8:ACAD:3::1**
28. Назначим адрес сервера DNS **dns-server 2a02:6b8::feed:0ff**
29. Назначим адрес ipv6 и префикс **address prefix 2001:DB8:ACAD:3::1/64**
>![17](https://user-images.githubusercontent.com/112701413/195101093-e7fc06c5-2bbe-44ef-a775-372a3fe6acd3.jpg)
30. Пропишим маршруты до подсетей R2 **ipv6 route 2001:db8:acad:3::1/64 2001:db8:acad:2::2**
>![16](https://user-images.githubusercontent.com/112701413/194767299-036d9d66-60ee-4a3d-b339-c5841c7cda57.jpg)

## Настройка R2 c отслеживания состояния и relay
1. Заходим в превилегированый режим **enable**
2. Переходим в режим конфигурации устройства **configure terminal**
3. Задаём имя для роутера **hostname R2**
>![9](https://user-images.githubusercontent.com/112701413/194762970-a22e0b02-6c87-405b-bbb1-10f850d84779.jpg)
4. Перейдем в интерфейс e0/0 **interface eth 0/0**
5. Зададем ipv6 адрес **ipv6 address 2001:db8:acad:2::2/64**
6. Зададим ipv6 *link-local* адрес **ipv6 address fe80::2 link-local**
7. Включим интерфейс **no shutdown**
>![10](https://user-images.githubusercontent.com/112701413/194762495-682e3a2c-319e-4912-9b63-16156a9e1035.jpg)
8. Проверим видит ли R2 R1 **do ping 2001:db8:acad:2::1**
>![11](https://user-images.githubusercontent.com/112701413/194762584-6034ee62-a2e6-475f-916a-093d3392bb60.jpg)
9. Перейдем в интерфейс e0/1 **interface eth 0/1**
10. Зададем ipv6 адрес **ipv6 address 2001:db8:acad:3::1/64**
11. Зададим ipv6 *link-local* адрес **ipv6 address fe80::1 link-local**
12. Установим флаг *managed* **ipv6 nd managed-config-flag**
13. Настроим получение ipv6 адресов с dhcpv6 сервера R1 **ipv6 dhcp relay destination 2001:DB8:ACAD:2::1**
14. Включим роутинг ipv6 **ipv6 unicast-routing**
>![18](https://user-images.githubusercontent.com/112701413/195159261-bdceff81-2671-4dd8-b156-80cd85a7b2f7.jpg)
15. Пропишим маршруты до подсетей R1 **ipv6 route 2001:db8:acad:1::1/64 2001:db8:acad:2::1**
>![15](https://user-images.githubusercontent.com/112701413/194767234-4934919c-6924-46cb-83b8-10c2ee31b85d.jpg)
16. На PC2 запросим ipv6 адрес **ip auto**
>![19](https://user-images.githubusercontent.com/112701413/195160700-13fd1c2a-6dbc-4c7f-b91a-b3ae47f310a6.jpg)
17. Проверим видит ли PC2 ---- PC1 **ping 2001:db8:acad:1:2050:79ff:fe66:680c**
>![14](https://user-images.githubusercontent.com/112701413/194767187-387421ab-920b-45e6-982f-c8bc6db77664.jpg)

