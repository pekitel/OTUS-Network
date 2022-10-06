# DHCP ipv6


#### Настройка [R1]
#### Настройка [R2]

## Схема сети

![ipv6](https://user-images.githubusercontent.com/112701413/193928748-a9eab94c-1479-4985-905b-4e1732a61fce.jpg)


  ## ipv6 address 
host | int | ip address |
:----:  | :----------: | :----: | 
R1 | e0/0 |2001:db8:acad:2::1/64 |
| | e0/1 | 2001:db8:acad:1::1/64 |
R2 | e0/0 | 2001:db8:acad:2::2/64 |
| | e0/1 | 2001:db8:acad:3::1/64 |
PC1 | eth0 | dhcp |
PC2 | eth0 | dhcp |

## Настройка R1
1. Заходим в превилегированый режим **enable**
2. Переходим в режим конфигурации устройства **configure terminal**
3. Задаём имя для роутера **hostname R1**
>![1](https://user-images.githubusercontent.com/112701413/194334686-025df8c6-a8ea-43d3-ba4b-909d7d871875.jpg)
4. Перейдем в интерфейс e0/0 **interface eth 0/0**
5. Зададем ipv6 адрес **ipv6 address 2001:db8:acad:2::1/64**
6. Включим интерфейс **no shutdown**
>![2](https://user-images.githubusercontent.com/112701413/194335846-e1c543bb-0e6a-458f-bb43-c6eb23a07927.jpg)
