# DHCP ipv6


#### Настройка [R1](https://github.com/pekitel/OTUS-Network/blob/main/%D0%94%D0%BE%D0%BC%D0%B0%D1%88%D0%BD%D0%B8%D0%B5%20%D1%80%D0%B0%D0%B1%D0%BE%D1%82%D1%8B/DHCP/dhcp%20ipv6/README.md#%D0%BD%D0%B0%D1%81%D1%82%D1%80%D0%BE%D0%B9%D0%BA%D0%B0-r1-1)
#### Настройка [R2]
#### Проверка [SLAAC PC1](https://github.com/pekitel/OTUS-Network/blob/main/%D0%94%D0%BE%D0%BC%D0%B0%D1%88%D0%BD%D0%B8%D0%B5%20%D1%80%D0%B0%D0%B1%D0%BE%D1%82%D1%8B/DHCP/dhcp%20ipv6/README.md#slaac)

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

## Настройка R1
1. Заходим в превилегированый режим **enable**
2. Переходим в режим конфигурации устройства **configure terminal**
3. Задаём имя для роутера **hostname R1**
>![1](https://user-images.githubusercontent.com/112701413/194334686-025df8c6-a8ea-43d3-ba4b-909d7d871875.jpg)
4. Перейдем в интерфейс e0/0 **interface eth 0/0**
5. Зададем ipv6 адрес **ipv6 address 2001:db8:acad:2::1/64**
6. Зададим ipv6 *link-local* адрес **ipv6 address fe80::1 link-local**
7. Включим интерфейс **no shutdown**
>![2](https://user-images.githubusercontent.com/112701413/194485974-970f3414-29b9-4f05-83e3-41c9cf835b1a.jpg)
## SLAAC 
8. Проверим получает ли PC1 ipv6 адрес через SLAAC
9. На PC1 введём команду **ip auto**
10. Посмотри настройки интерфейса **show ipv6** 
>![3](https://user-images.githubusercontent.com/112701413/194756191-afb6a6d1-c9a8-476a-bd30-ec022da1d146.jpg)
11. 
