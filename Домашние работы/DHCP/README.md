# DHCP
  1. Настройка DHCP ipv4
  2. Настройка DHCP ipv6
  
  ## Схема сети
  
![dhcp](https://user-images.githubusercontent.com/112701413/193837728-b23ae5df-c30f-409e-9d04-511a8697b7ea.jpg)

  ## ipv4 address 
host | int | VLAN | name | ip address | excluded-address | DHCP |
:----: | :---: | :---: | :----------: | :---: | :---: | :---: 
R1 | Gi0/0 | | |10.0.0.1/30 | |no
| | Gi0/1.100 | 100 | User | 192.168.100.0/24 | 192.168.100.1-10; 192.168.100.254 | yes
| | Gi0/1.200 | 200 | MGMT |192.168.200.0/24 | | no
| | Gi0/1.1000 | 1000 | Native || |no
R2 | Gi0/0 | | |10.0.0.2/30 | | no
| | Gi0/1.100 | 100 | User | 172.16.100.0/24 | 172.16.100.1-10; 172.16.100.254 |  yes
| | Gi0/1.200 | 200 | MGMT |172.16.200.0/24 | | no
| | Gi0/1.1000 | 1000 | Native | | | no
Sw1 | e0/0 | 200| MGMT | 192.168.200.10/24 | | no
|| e0/1 | 100| User | | | no
Sw2 | e0/0 | 200| MGMT | 172.16.200.10/24 | | no
|| e0/1 | 100| User | | | no
PC1 | eth0 | 100 | User | | | yes
PC2 | eth0 | 100 | User | | | yes
  ## ipv6 address 
host | int | name | ip address | DHCP |
:----:  | :---: | :----------: | :----: | :---: 
R3 | e0/0 | |2001:db8:acad:2::1/64 | |
| | e0/1 | User | 2001:db8:acad:1::1/64 |  yes
R4 | e0/0 | | 2001:db8:acad:2::2/64 | |
| | e0/1 | User | 2001:db8:acad:3::1/64 |  no

## Настройка R1
1. Заходим в превилегированый режим **enable**
2. Переходим в режим конфигурации устройства **configure terminal**
3. Задаём имя для роутера **hostname R1**
>![1](https://user-images.githubusercontent.com/112701413/189698770-fa6f5f81-f215-4878-98aa-78ae22549d72.jpg)
4. Перейдем в интерфейс Gi0/0 **interface gigabitEthernet 0/0**
5. Зададем ip адрес **ip address 10.0.0.1 255.255.255.252**
6. Включим интерфейс **no shutdown**
>![1](https://user-images.githubusercontent.com/112701413/193856079-d06ecdb4-4efc-46f3-a9b0-b2b811911b29.jpg)
7. 
