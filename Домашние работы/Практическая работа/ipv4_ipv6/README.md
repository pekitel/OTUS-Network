# Задание

1. Разработаете и задокументируете адресное пространство для лабораторного стенда
2. Настроите ip адреса на каждом активном порту
3. Настроите каждый VPC в каждом офисе в своем VLAN.
4. Настроите VLAN управления для сетевых устройств
5. Настроите сети офисов так, чтобы не возникало broadcast штормов, а использование линков было максимально оптимизировано
6. Используете ipv4 и ipv6


1.1 [Провайдеры ipv4](https://github.com/pekitel/OTUS-Network/blob/main/%D0%94%D0%BE%D0%BC%D0%B0%D1%88%D0%BD%D0%B8%D0%B5%20%D1%80%D0%B0%D0%B1%D0%BE%D1%82%D1%8B/%D0%9F%D1%80%D0%B0%D0%BA%D1%82%D0%B8%D1%87%D0%B5%D1%81%D0%BA%D0%B0%D1%8F%20%D1%80%D0%B0%D0%B1%D0%BE%D1%82%D0%B0/ipv4_ipv6/README.md#%D0%BF%D1%80%D0%BE%D0%B2%D0%B0%D0%B9%D0%B4%D0%B5%D1%80%D1%8B-ipv4)

1.2 [Провайдеры ipv6](https://github.com/pekitel/OTUS-Network/blob/main/%D0%94%D0%BE%D0%BC%D0%B0%D1%88%D0%BD%D0%B8%D0%B5%20%D1%80%D0%B0%D0%B1%D0%BE%D1%82%D1%8B/%D0%9F%D1%80%D0%B0%D0%BA%D1%82%D0%B8%D1%87%D0%B5%D1%81%D0%BA%D0%B0%D1%8F%20%D1%80%D0%B0%D0%B1%D0%BE%D1%82%D0%B0/ipv4_ipv6/README.md#%D0%BF%D1%80%D0%BE%D0%B2%D0%B0%D0%B9%D0%B4%D0%B5%D1%80%D1%8B-ipv6)

2.1 [Москва ipv4](https://github.com/pekitel/OTUS-Network/blob/main/%D0%94%D0%BE%D0%BC%D0%B0%D1%88%D0%BD%D0%B8%D0%B5%20%D1%80%D0%B0%D0%B1%D0%BE%D1%82%D1%8B/%D0%9F%D1%80%D0%B0%D0%BA%D1%82%D0%B8%D1%87%D0%B5%D1%81%D0%BA%D0%B0%D1%8F%20%D1%80%D0%B0%D0%B1%D0%BE%D1%82%D0%B0/ipv4_ipv6/README.md#%D0%BC%D0%BE%D1%81%D0%BA%D0%B2%D0%B0-ipv4)

2.2 [Москва ipv6](https://github.com/pekitel/OTUS-Network/blob/main/%D0%94%D0%BE%D0%BC%D0%B0%D1%88%D0%BD%D0%B8%D0%B5%20%D1%80%D0%B0%D0%B1%D0%BE%D1%82%D1%8B/%D0%9F%D1%80%D0%B0%D0%BA%D1%82%D0%B8%D1%87%D0%B5%D1%81%D0%BA%D0%B0%D1%8F%20%D1%80%D0%B0%D0%B1%D0%BE%D1%82%D0%B0/ipv4_ipv6/README.md#%D0%BC%D0%BE%D1%81%D0%BA%D0%B2%D0%B0-ipv6)

3.1 [Санкт-Петербург ipv4](https://github.com/pekitel/OTUS-Network/blob/main/%D0%94%D0%BE%D0%BC%D0%B0%D1%88%D0%BD%D0%B8%D0%B5%20%D1%80%D0%B0%D0%B1%D0%BE%D1%82%D1%8B/%D0%9F%D1%80%D0%B0%D0%BA%D1%82%D0%B8%D1%87%D0%B5%D1%81%D0%BA%D0%B0%D1%8F%20%D1%80%D0%B0%D0%B1%D0%BE%D1%82%D0%B0/ipv4_ipv6/README.md#%D1%81%D0%B0%D0%BD%D0%BA%D1%82-%D0%BF%D0%B5%D1%82%D0%B5%D1%80%D0%B1%D1%83%D1%80%D0%B3-ipv4)

3.2 [Санкт-Петербург ipv6](https://github.com/pekitel/OTUS-Network/blob/main/%D0%94%D0%BE%D0%BC%D0%B0%D1%88%D0%BD%D0%B8%D0%B5%20%D1%80%D0%B0%D0%B1%D0%BE%D1%82%D1%8B/%D0%9F%D1%80%D0%B0%D0%BA%D1%82%D0%B8%D1%87%D0%B5%D1%81%D0%BA%D0%B0%D1%8F%20%D1%80%D0%B0%D0%B1%D0%BE%D1%82%D0%B0/ipv4_ipv6/README.md#%D1%81%D0%B0%D0%BD%D0%BA%D1%82-%D0%BF%D0%B5%D1%82%D0%B5%D1%80%D0%B1%D1%83%D1%80%D0%B3-ipv6)

4.1 [Чокурдах ipv4](https://github.com/pekitel/OTUS-Network/blob/main/%D0%94%D0%BE%D0%BC%D0%B0%D1%88%D0%BD%D0%B8%D0%B5%20%D1%80%D0%B0%D0%B1%D0%BE%D1%82%D1%8B/%D0%9F%D1%80%D0%B0%D0%BA%D1%82%D0%B8%D1%87%D0%B5%D1%81%D0%BA%D0%B0%D1%8F%20%D1%80%D0%B0%D0%B1%D0%BE%D1%82%D0%B0/ipv4_ipv6/README.md#%D1%87%D0%BE%D0%BA%D1%83%D1%80%D0%B4%D0%B0%D1%85-ipv4)

4.2 [Чокурдах ipv6](https://github.com/pekitel/OTUS-Network/blob/main/%D0%94%D0%BE%D0%BC%D0%B0%D1%88%D0%BD%D0%B8%D0%B5%20%D1%80%D0%B0%D0%B1%D0%BE%D1%82%D1%8B/%D0%9F%D1%80%D0%B0%D0%BA%D1%82%D0%B8%D1%87%D0%B5%D1%81%D0%BA%D0%B0%D1%8F%20%D1%80%D0%B0%D0%B1%D0%BE%D1%82%D0%B0/ipv4_ipv6/README.md#%D1%87%D0%BE%D0%BA%D1%83%D1%80%D0%B4%D0%B0%D1%85-ipv6)

5.1 [Лабытнанги ipv4](https://github.com/pekitel/OTUS-Network/blob/main/%D0%94%D0%BE%D0%BC%D0%B0%D1%88%D0%BD%D0%B8%D0%B5%20%D1%80%D0%B0%D0%B1%D0%BE%D1%82%D1%8B/%D0%9F%D1%80%D0%B0%D0%BA%D1%82%D0%B8%D1%87%D0%B5%D1%81%D0%BA%D0%B0%D1%8F%20%D1%80%D0%B0%D0%B1%D0%BE%D1%82%D0%B0/ipv4_ipv6/README.md#%D0%BB%D0%B0%D0%B1%D1%8B%D1%82%D0%BD%D0%B0%D0%BD%D0%B3%D0%B8-ipv4)

5.2 [Лабытнанги ipv6](https://github.com/pekitel/OTUS-Network/blob/main/%D0%94%D0%BE%D0%BC%D0%B0%D1%88%D0%BD%D0%B8%D0%B5%20%D1%80%D0%B0%D0%B1%D0%BE%D1%82%D1%8B/%D0%9F%D1%80%D0%B0%D0%BA%D1%82%D0%B8%D1%87%D0%B5%D1%81%D0%BA%D0%B0%D1%8F%20%D1%80%D0%B0%D0%B1%D0%BE%D1%82%D0%B0/ipv4_ipv6/README.md#%D0%BB%D0%B0%D0%B1%D1%8B%D1%82%D0%BD%D0%B0%D0%BD%D0%B3%D0%B8-ipv6)


#### Configs

[конфигурации оборудования Провайдеры](https://github.com/pekitel/OTUS-Network/tree/main/%D0%94%D0%BE%D0%BC%D0%B0%D1%88%D0%BD%D0%B8%D0%B5%20%D1%80%D0%B0%D0%B1%D0%BE%D1%82%D1%8B/%D0%9F%D1%80%D0%B0%D0%BA%D1%82%D0%B8%D1%87%D0%B5%D1%81%D0%BA%D0%B0%D1%8F%20%D1%80%D0%B0%D0%B1%D0%BE%D1%82%D0%B0/ipv4_ipv6/configs/%D0%9F%D1%80%D0%BE%D0%B2%D0%B0%D0%B9%D0%B4%D0%B5%D1%80%D1%8B)

[конфигурации оборудования MSK](https://github.com/pekitel/OTUS-Network/tree/main/%D0%94%D0%BE%D0%BC%D0%B0%D1%88%D0%BD%D0%B8%D0%B5%20%D1%80%D0%B0%D0%B1%D0%BE%D1%82%D1%8B/%D0%9F%D1%80%D0%B0%D0%BA%D1%82%D0%B8%D1%87%D0%B5%D1%81%D0%BA%D0%B0%D1%8F%20%D1%80%D0%B0%D0%B1%D0%BE%D1%82%D0%B0/ipv4_ipv6/configs/MSK)

[конфигурации оборудования SPB](https://github.com/pekitel/OTUS-Network/tree/main/%D0%94%D0%BE%D0%BC%D0%B0%D1%88%D0%BD%D0%B8%D0%B5%20%D1%80%D0%B0%D0%B1%D0%BE%D1%82%D1%8B/%D0%9F%D1%80%D0%B0%D0%BA%D1%82%D0%B8%D1%87%D0%B5%D1%81%D0%BA%D0%B0%D1%8F%20%D1%80%D0%B0%D0%B1%D0%BE%D1%82%D0%B0/ipv4_ipv6/configs/SPB)

[конфигурации оборудования Чокурдах](https://github.com/pekitel/OTUS-Network/tree/main/%D0%94%D0%BE%D0%BC%D0%B0%D1%88%D0%BD%D0%B8%D0%B5%20%D1%80%D0%B0%D0%B1%D0%BE%D1%82%D1%8B/%D0%9F%D1%80%D0%B0%D0%BA%D1%82%D0%B8%D1%87%D0%B5%D1%81%D0%BA%D0%B0%D1%8F%20%D1%80%D0%B0%D0%B1%D0%BE%D1%82%D0%B0/ipv4_ipv6/configs/%D0%A7%D0%BE%D0%BA%D1%83%D1%80%D0%B4%D0%B0%D1%85)

[конфигурации оборудования Лабытнанги](https://github.com/pekitel/OTUS-Network/tree/main/%D0%94%D0%BE%D0%BC%D0%B0%D1%88%D0%BD%D0%B8%D0%B5%20%D1%80%D0%B0%D0%B1%D0%BE%D1%82%D1%8B/%D0%9F%D1%80%D0%B0%D0%BA%D1%82%D0%B8%D1%87%D0%B5%D1%81%D0%BA%D0%B0%D1%8F%20%D1%80%D0%B0%D0%B1%D0%BE%D1%82%D0%B0/ipv4_ipv6/configs/%D0%9B%D0%B0%D0%B1%D1%8B%D1%82%D0%BD%D0%B0%D0%BD%D0%B3%D0%B8)

#### **По данной схеме офис Москва и Санкт-Петербург имеют свои pool адресов ipv4 и ipv6 адресов, а офисы Лабытнанги и Чокурдах арендуют адреса ipv4 и ipv6 у провайдера Триада**

## **Схема сети ipv4**

>![ipv4](https://user-images.githubusercontent.com/112701413/203728472-1ed0277e-aa87-4101-ba3c-89b9671099b7.jpg)



## Адресное пространство ipv4


### Провайдеры ipv4


| Hosts      | Ports    | Network IPv4   |     Description       | Provider     | Loopback      |    
|:----------:|:--------:|:--------------:|:--------------------- |:------------:|:-------------:|    
| R22        | e0/0     | 82.138.2.1/30  | to --> R14 MSK        | Киторн       | 82.138.1.22   |
|            | e0/1     | 82.138.2.5/30  | to --> R21 Lamas      |              |               |
|            | e0/2     | 109.72.1.18/30 | to --> R23 Triada     |              |               |
| R21        | e0/0     | 77.94.165.1/30 | to --> R15 MSK        | Ламас        | 77.94.164.21  |
|            | e0/1     | 82.138.2.6/30  | to --> R22 Kitorn     |              |               |
|            | e0/2     | 109.72.1.22/30 | to --> R24 Triada     |              |               |
| R23        | e0/0     | 109.72.1.17/30 | to --> R22 Kitorn     | Триада       | 109.72.255.23 |
|            | e0/1     | 109.72.1.1/30  | to --> R25            |              |               |
|            | e0/2     | 109.72.1.14/30 | to --> R24            |              |               |
| R25        | e0/0     | 109.72.1.2/30  | to --> R23            |              | 109.72.255.25 |
|            | e0/1     | 109.72.1.25/30 | to --> R27 Labytnangi |              |               |
|            | e0/2     | 109.72.1.5/30  | to --> R26            |              |               |
|            | e0/3     | 109.72.1.29/30 | to --> R28 Chukordah  |              |               |
| R26        | e0/0     | 109.72.1.9/30  | to --> R24            |              | 109.72.255.26 |
|            | e0/1     | 109.72.1.33/30 | to --> R28 Chukordah  |              |               |
|            | e0/2     | 109.72.1.6/30  | to --> R25            |              |               |
|            | e0/3     | 109.72.1.41/30 | to --> R18 SPB        |              |               |
| R24        | e0/0     | 109.72.1.21/30 | to --> R21 Lamas      |              | 109.72.255.24 |
|            | e0/1     | 109.72.1.10/30 | to --> R26            |              |               |
|            | e0/2     | 109.72.1.13/30 | to --> R23            |              |               |
|            | e0/3     | 109.72.1.27/30 | to --> R18 SPB        |              |               |


### Москва ipv4

#### ***Pool ip адресов 77.37.144.0/23***

| Hosts      | Ports    | Network IPv4    |     Description       | vlan         | Loopback     |
|:----------:|:--------:|:---------------:|:--------------------- |:------------:|:------------:|
| R14        | e0/0     | 10.10.1.5/30    | to --> R12            |              | 77.37.144.14 |
|            | e0/1     | 10.10.1.9/30    | to --> R13            |              |              |
|            | e0/2     | 82.138.2.2/30   | to --> R22 Kitorn     |              |              |
|            | e0/3     | 10.10.1.1/30    | to --> R19            |              |              |
| R15        | e0/0     | 10.10.1.17/30   | to --> R13            |              | 77.37.144.15 |
|            | e0/1     | 10.10.1.13/30   | to --> R12            |              |              |
|            | e0/2     | 77.94.165.2/30  | to --> R21 Lamas      |              |              |
|            | e0/3     | 10.10.1.21/30   | to --> R20            |              |              |
| R19        | e0/0     | 10.10.1.2/30    | to --> R14            |              | 77.37.144.19 |
| R12        | e0/2     | 10.10.1.6/30    | to --> R14            |              | 77.37.144.12 |
|            | e0/3     | 10.10.1.14/30   | to --> R15            |              |              |
|            | e0/0.10  | 172.16.3.1/28   | to --> SW4            |              |              |
|            | e0/0.20  | 172.16.3.17/25  | to --> SW4            |              |              |
| R13        | e0/2     | 10.10.1.18/30   | to --> R15            |              | 77.37.144.13 |
|            | e0/3     | 10.10.1.10/30   | to --> R14            |              |              |
|            | e0/0.99  | 172.16.30.1/29  | to --> SW5 MGMT       |              |              |
| R20        | e0/0     | 10.10.1.22/30   | to --> R15            |              | 77.37.144.20 |
| SW4        | vlan 99  | 172.16.30.4/29  |                       | 99 MGMT      |              |
|            | e0/0     |                 | to --> SW5            | 10,20,99,777 |              |
|            | e0/1     |                 | to --> SW2            | 10,20,99,777 |              |
|            | e0/2     |                 | Port channel 1        | 10,20,99,777 |              |
|            | e0/3     |                 | Port channel 1        | 10,20,99,777 |              |
|            | e1/0     |                 | to --> R12            | 10,20        |              |
| SW5        | vlan 99  | 172.16.30.5/29  |                       |              |              |
|            | e0/0     |                 | to --> SW2            | 10,20,99,777 |              |
|            | e0/1     |                 | to --> SW3            | 10,20,99,777 |              |
|            | e0/2     |                 | Port channel 1        | 10,20,99,777 |              |
|            | e0/3     |                 | Port channel 1        | 10,20,99,777 |              |
|            | e1/0     |                 | to --> R13            | 99           |              |
| SW3        | vlan 99  | 172.16.30.3/29  |                       | 99           |              |
|            | e0/0     |                 | to --> SW4            | 10,20,99,777 |              |
|            | e0/1     |                 | to --> SW5            | 10,20,99,777 |              |
|            | e0/2     |                 | to --> VPC1           | 10           |              |
| SW2        | vlan 99  | 172.16.3.2/29   |                       | 99           |              |
| SW2        | e0/0     |                 | to --> SW5            | 10,20,99,777 |              |
|            | e0/1     |                 | to --> SW4            | 10,20,99,777 |              |
|            | e0/2     |                 | to --> VPC7           | 20           |              |
|VPC1        | eth0     | DHCP            |                       | 10           |              |
|VPC7        | eth0     | DHCP            |                       | 20           |              |



### Санкт-Петербург ipv4

#### ***Pool ip адресов 33.72.66.0/24***

| Hosts      | Ports    | Network IPv4   |     Description       | vlan         | Loopback    |
|:----------:|:--------:|:--------------:|:--------------------- |:------------:|:-----------:|
| R18        | e0/0     | 10.10.2.5/30   | to --> R16            |              | 33.72.66.17 |
|            | e0/1     | 10.10.2.1/30   | to --> R17            |              |             |
|            | e0/2     | 109.72.1.38/30 | to --> R24 Triada     |              |             |
|            | e0/3     | 109.72.1.42/30 | to --> R26 Triada     |              |             |
| R17        | e0/0.10  | 172.16.1.1/28  | to --> SW9            |              | 33.72.66.18 |
|            | e0/0.20  | 172.16.1.16/28 | to --> SW9            |              |             |
|            | e0/1     | 10.10.2.2/30   | to --> R18            |              |             |
| R16        | e0/0.99  | 172.16.10.1/29 | to --> SW10 MGMT      |              | 33.72.66.19 |
|            | e0/1     | 10.10.2.6/30   | to --> R18            |              |             |
|            | e0/3     | 10.10.2.9/30   | to --> R32            |              |             |
| R32        | e0/0     | 10.10.2.10/30  | to --> R16            |              | 33.72.66.20 |
| SW9        | vlan 99  | 172.16.10.2/29 |                       | 99 MGMT      |             |
|            | e1/0     |                | to --> R17            | 10,20,777    |             |
|            | e0/0     |                | Port channel 1        | 10,20,99,777 |             |
|            | e0/1     |                | Port channel 1        | 10,20,99,777 |             |
|            | e0/2     |                | to --> VPC8           | 10           |             |
| SW10       | vlan 99  | 172.16.10.3/29 |                       | 99 MGMT      |             |
|            | e0/3     |                | to --> R16            | 99           |             |
|            | e0/0     |                | Port channel 1        | 10,20,99,777 |             |
|            | e0/1     |                | Port channel 1        | 10,20,99,777 |             |
|            | e0/2     |                | to --> VPC            | 20           |             |
| VPC8       | eth0     | dhcp           |                       | 10           |             |
| VPC        | eth0     | dhcp           |                       | 20           |             |




### Чокурдах ipv4

#### ***ip адрес 109.72.67.28***

| Hosts      | Ports    | Network IPv4   | Description           | vlan         | Loopback    |
|:----------:|:--------:|:--------------:|:---------------------:|:------------:|:-----------:|
| R28        | e0/0     | 109.72.1.34/30 | to --> R26            |              | 109.72.67.28|
|            | e0/1     | 109.72.1.30/30 | to --> R25            |              |             |
|            | e0/2.10  | 172.16.2.1/28  | to --> SW29           |              |             |
|            | e0/2.20  | 172.16.2.17/29 | to --> SW29           |              |             |
|            | e0/2.99  | 172.16.20.1/30 | to --> SW29 MGMT      |              |             |
| SW29       | vlan 99  | 172.16.20.2/30 |                       | 99 MGMT      |             |
|            | e0/0     |                | to --> VPC30          | 10           |             |
|            | e0/1     |                | to --> VPC31          | 20           |             |
|            | e0/2     |                | to --> R28            | 10,20,99,777 |             |
| VPC30      | eth0     | dhcp           |                       | 10           |             |
| VPC31      | eth0     | dhcp           |                       | 20           |             |



### Лабытнанги ipv4

#### ***ip адрес 109.72.68.27***

| Hosts      | Ports    | Network IPv4   | Description           | vlan         | Loopback    |
|:----------:|:--------:|:--------------:|:---------------------:|:------------:|:-----------:|
| R27        | e0/0     | 109.72.1.26/30 | to --> R25            |              | 109.72.68.27|



## **Схема сети ipv6**

>![ipv6](https://user-images.githubusercontent.com/112701413/201694718-b85ad1d6-3b38-4db4-bd74-be6fe650344c.jpg)


## Адресное пространство ipv6

### Провайдеры ipv6


|     Hosts  | Ports    | Network IPv6             |link-local|     Description       | Provider     | Loopback    | POOL адресов ipv6    |
|:----------:|:--------:|:------------------------:|:--------:|:---------------------:|:------------:|:-----------:|:--------------------:|   
| **R22**    | e0/0     | 2000:ABCD:FFBB:FFFF:1::1 | FE80::22 | to --> R14 MSK        | ***Киторн*** | fe80:1::22  | 2000:ABCD:FFBB::0/48 |
|            | e0/1     | 2000:ABCD:FFBB:FFFF:2::1 | FE80::22 | to --> R21 Lamas      |              |             |                      |
|            | e0/2     | 2002:ABCD:EEBB:FFFF:8::2 | FE80::22 | to --> R23 Triada     |              |             |                      |
| **R21**    | e0/0     | 1999:ABCD:EEBB:FFFF:1::1 | FE80::21 | to --> R15 MSK        | ***Ламас***  | fe80:1::21  | 1999:ABCD:FFBB::0/48 |
|            | e0/1     | 2000:ABCD:FFBB:FFFF:2::2 | FE80::21 | to --> R22 Kitorn     |              |             |                      |
|            | e0/2     | 2002:ABCD:EEBB:FFFF:9::2 | FE80::22 | to --> R24 Triada     |              |             |                      |
| **R23**    | e0/0     | 2002:ABCD:EEBB:FFFF:8::1 | FE80::23 | to --> R22 Kitorn     | ***Триада*** | fe80:1::23  | 2002:ABCD:FFBB::0/48 |
|            | e0/1     | 2002:ABCD:EEBB:FFFF:1::1 | FE80::23 | to --> R25            |              |             |                      |
|            | e0/2     | 2002:ABCD:EEBB:FFFF:7::2 | FE80::23 | to --> R24            |              |             |                      |
| **R25**    | e0/0     | 2002:ABCD:EEBB:FFFF:1::2 | FE80::25 | to --> R23            |              | fe80:1::25  |                      |
|            | e0/1     | 2002:ABCD:EEBB:FFFF:3::1 | FE80::25 | to --> R27 Labytnangi |              |             |                      |
|            | e0/2     | 2002:ABCD:EEBB:FFFF:5::1 | FE80::25 | to --> R26            |              |             |                      |
|            | e0/3     | 2002:ABCD:EEBB:FFFF:2::1 | FE80::25 | to --> R28 Chukordah  |              |             |                      |
| **R26**    | e0/0     | 2002:ABCD:EEBB:FFFF:6::1 | FE80::26 | to --> R24            |              | fe80:1::26  |                      |
|            | e0/1     | 2002:ABCD:EEBB:FFFF:4::1 | FE80::26 | to --> R28 Chukordah  |              |             |                      |
|            | e0/2     | 2002:ABCD:EEBB:FFFF:5::2 | FE80::26 | to --> R25            |              |             |                      |
|            | e0/3     | 2002:ABCD:EEBB:FFFF:B::1 | FE80::26 | to --> R18 SPB        |              |             |                      |
| **R24**    | e0/0     | 2002:ABCD:EEBB:FFFF:9::1 | FE80::24 | to --> R21 Lamas      |              | fe80:1::24  |                      |
|            | e0/1     | 2002:ABCD:EEBB:FFFF:6::2 | FE80::26 | to --> R26            |              |             |                      |
|            | e0/2     | 2002:ABCD:EEBB:FFFF:7::1 | FE80::24 | to --> R23            |              |             |                      |
|            | e0/3     | 2002:ABCD:EEBB:FFFF:A::1 | FE80::24 | to --> R18 SPB        |              |             |                      |



### Москва ipv6

#### ***Pool ipv6 адресов 2001:ABCD:EEBB:AAAA::0/64***


| Hosts      | Ports    | Network IPv6                   | link-local |     Description       | vlan         | Loopback   |
|:----------:|:--------:|:------------------------------:|:----------:|:---------------------:|:------------:|:----------:|
| R14        | e0/0     | 2001:ABCD:EEBB:AAAA:2::1/80    | FE80::14   | to --> R12            |              | FE80:1::14 |
|            | e0/1     | 2001:ABCD:EEBB:AAAA:3::1/80    | FE80::14   | to --> R13            |              |            |
|            | e0/2     | 2000:ABCD:FFBB:FFFF:1::2/80    | FE80::14   | to --> R22 Kitorn     |              |            |
|            | e0/3     | 2001:ABCD:EEBB:AAAA:1::1/80    | FE80::14   | to --> R19            |              |            |
| R15        | e0/0     | 2001:ABCD:EEBB:AAAA:5::1/80    | FE80::15   | to --> R13            |              | FE80:1::15 |
|            | e0/1     | 2001:ABCD:EEBB:AAAA:4::1/80    | FE80::15   | to --> R12            |              |            |
|            | e0/2     | 1999:ABCD:EEBB:FFFF:1::2/80    | FE80::15   | to --> R21 Lamas      |              |            |
|            | e0/3     | 2001:ABCD:EEBB:AAAA:6::1/80    | FE80::15   | to --> R20            |              |            |
| R19        | e0/0     | 2001:ABCD:EEBB:AAAA:1::2/80    | FE80::19   | to --> R14            |              | FE80:1::19 |
| R12        | e0/2     | 2001:ABCD:EEBB:AAAA:2::2/80    | FE80::12   | to --> R14            |              | FE80:1::12 |
|            | e0/3     | 2001:ABCD:EEBB:AAAA:4::2/80    | FE80::12   | to --> R15            |              |            |
|            | e0/0.10  | 2001:ABCD:EEBB:AAAA:2222::1/80 | FE80::12   | to --> SW4            |              |            |
|            | e0/0.20  | 2001:ABCD:EEBB:AAAA:3333::1/80 | FE80::12   | to --> SW4            |              |            |
| R13        | e0/2     | 2001:ABCD:EEBB:AAAA:5::2/80    | FE80::13   | to --> R15            |              | FE80:1::13 |
|            | e0/3     | 2001:ABCD:EEBB:AAAA:3::2/80    | FE80::13   | to --> R14            |              |            |
|            | e0/0.99  | 2001:ABCD:EEBB:AAAA:1111::1/80 | FE80::13   | to --> SW5 MGMT       |              |            |
|            | E0/0.777 |                                |            | NATIVE                | 777          |            |
| R20        | e0/0     | 2001:ABCD:EEBB:AAAA:6::2/80    | FE80::20   | to --> R15            |              | FE80:1::20 |
| SW4        | vlan 99  | 2001:ABCD:EEBB:AAAA:1111::4/80 | FE80::4    | MGMT                  | 99           | FE80:1::4  |
|            | e0/0     |                                |            | to --> SW5            | 10,20,99,777 |            |
|            | e0/1     |                                |            | to --> SW2            | 10,20,99,777 |            |
|            | e0/2     |                                |            | Port channel 1        | 10,20,99,777 |            |
|            | e0/3     |                                |            | Port channel 1        | 10,20,99,777 |            |
|            | e1/0     |                                |            | to --> R12            | 10,20,777    |            |
| SW5        | vlan 99  | 2001:ABCD:EEBB:AAAA:1111::5/80 | FE80::5    | MGMT                  | 99           | FE80:1::5  |
|            | e0/0     |                                |            | to --> SW2            | 10,20,99,777 |            |
|            | e0/1     |                                |            | to --> SW3            | 10,20,99,777 |            |
|            | e0/2     |                                |            | Port channel 1        | 10,20,99,777 |            |
|            | e0/3     |                                |            | Port channel 1        | 10,20,99,777 |            |
|            | e1/0     |                                |            | to --> R13            | 99,777       |            |
| SW3        | vlan 99  | 2001:ABCD:EEBB:AAAA:1111::3/80 | FE80::5    | MGMT                  | 99           | FE80:1::3  |
|            | e0/0     |                                |            | to --> SW4            | 10,20,99,777 |            |
|            | e0/1     |                                |            | to --> SW5            | 10,20,99,777 |            |
|            | e0/2     |                                |            | to --> VPC1           | 10           |            |
| SW2        | vlan 99  | 2001:ABCD:EEBB:AAAA:1111::2/80 | FE80::2    | MGMT                  | 99           | FE80:1::2  |
|            | e0/0     |                                |            | to --> SW5            | 10,20,99,777 |            |
|            | e0/1     |                                |            | to --> SW4            | 10,20,99,777 |            |
|            | e0/2     |                                |            | to --> VPC7           | 20           |            |
| VPC1       | eth0     | DHCP                           |            |                       | 10           |            |
| VPC7       | eth0     | DHCP                           |            |                       | 20           |            |


### Санкт-Петербург ipv6

#### ***Pool ipv6 адресов 2003:ABCD:EEBB:BBBB::0/64***

| Hosts      | Ports    | Network IPv6                    |link-local|     Description       | vlan         | Loopback    |
|:----------:|:--------:|:-------------------------------:|:--------:|:---------------------:|:------------:|:-----------:|
| R18        | e0/0     | 2003:ABCD:EEBB:BBBB:2::1/80     | FE80::18 | to --> R16            |              | FE80:1::18  |
|            | e0/1     | 2003:ABCD:EEBB:BBBB:1::1/80     | FE80::18 | to --> R17            |              |             |
|            | e0/2     | 2002:ABCD:EEBB:FFFF:A::2/80     | FE80::18 | to --> R24 Triada     |              |             |
|            | e0/3     | 2002:ABCD:EEBB:FFFF:B::2/80     | FE80::18 | to --> R26 Triada     |              |             |
| R17        | e0/1     | 2003:ABCD:EEBB:BBBB:1::2/80     | FE80::17 | to --> R18            |              | FE80:1::17  |
|            | e0/0.10  | 2003:ABCD:EEBB:BBBB:2222::1/80  | FE80::17 | to --> SW9            |              |             |
|            | e0/0.20  | 2003:ABCD:EEBB:BBBB:3333::1/80  | FE80::17 | to --> SW9            |              |             |
| R16        | e0/1     | 2003:ABCD:EEBB:BBBB:2::2/80     | FE80::16 | to --> R18            |              | FE80:1::16  |
|            | e0/3     | 2003:ABCD:EEBB:BBBB:3::1/80     | FE80::16 | to --> R32            |              |             |
|            | e0/0.99  | 2003:ABCD:EEBB:BBBB:1111::1/80  | FE80::16 | to --> SW10 MGMT      |              |             |
|            | e0/0.777 |                                 |          | NATIVE                | 777          |             |
| R32        | e0/0     | 2003:ABCD:EEBB:BBBB:3::2/80     | FE80::32 | to --> R16            |              | FE80:1::32  |
| SW9        | vlan 99  | 2003:ABCD:EEBB:BBBB:3333::9/80  | FE80::9  | MGMT                  | 99           | FE80:1::9   |
|            | e0/0     |                                 |          | Port channel 1        | 10,20,99,777 |             |
|            | e0/1     |                                 |          | Port channel 1        | 10,20,99,777 |             |
|            | e0/2     |                                 |          | to --> VPC8           | 10           |             |
|            | e1/0     |                                 |          | to --> R17            | 10,20,777    |             |
| SW10       | vlan 99  | 2003:ABCD:EEBB:BBBB:3333::10/80 | FE80::10 | MGMT                  | 99           | FE80:1::10  |
|            | e0/0     |                                 |          | Port channel 1        | 10,20,99,777 |             |
|            | e0/1     |                                 |          | Port channel 1        | 10,20,99,777 |             |
|            | e0/2     |                                 |          | to --> VPC            | 20           |             |
|            | e0/3     |                                 |          | to --> R16            | 99,777       |             |
| VPC8       | eth0     | DHCP                            |          |                       | 10           |             |
| VPC        | eth0     | DHCP                            |          |                       | 20           |             |


### Лабытнанги ipv6

#### ***Pool ipv6 адресов 2002:ABCD:EEBB:BBBB::0/64***

| Hosts      | Ports    | Network IPv6                | link-local |     Description       | vlan         | Loopback   |
|:----------:|:--------:|:---------------------------:|:----------:|:---------------------:|:------------:|:----------:|
| R27        | e0/0     | 2002:ABCD:EEBB:FFFF:3::2/80 | FE80::27   | to --> R25 Triada     |              | FE80:1:27  |


### Чокурдах ipv6

#### ***Pool ipv6 адресов 2002:ABCD:EEBB:AAAA::0/64***

| Hosts      | Ports    | Network IPv6                    |link-local|     Description       | vlan         | Loopback   |
|:----------:|:--------:|:-------------------------------:|:--------:|:---------------------:|:------------:|:----------:|
| R28        | e0/0     | 2002:ABCD:EEBB:FFFF:4::2/80     | FE80::28 | to --> 28 Triada      |              | FE80:1::28 |
|            | e0/1     | 2002:ABCD:EEBB:FFFF:2::2/80     | FE80::28 | to --> 28 Triada      |              |            |
|            | e0/2.10  | 2002:ABCD:EEBB:AAAA:2222::1/80  | FE80::28 | to --> SW29           |              |            |
|            | e0/2.20  | 2002:ABCD:EEBB:AAAA:3333::1/80  | FE80::28 | to --> SW29           |              |            |
|            | e0/2.99  | 2002:ABCD:EEBB:AAAA:1111::1/80  | FE80::28 | to --> SW29 MGMT      |              |            |
|            | e0/2.777 |                                 |          | NATIVE                |              |            |
| SW29       | vlan 99  | 2002:ABCD:EEBB:AAAA:1111::29/80 | FE80::29 | MGMT                  | 99           | FE80:1::29 |
|            | e0/0     |                                 |          | to --> VPC30          | 10           |            |
|            | e0/1     |                                 |          | to --> VPC31          | 20           |            |
|            | e0/2     |                                 |          | to --> R28            | 10,20,99,777 |            |
| VPC30      | eth0     | DHCP                            |          |                       | 10           |            |
| VPC31      | eth0     | DHCP                            |          |                       | 20           |            |



