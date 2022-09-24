# DHCP
  1. Настройка DHCP ipv4
  2. Настройка DHCP ipv6
  
  ## Схема сети
  
![dhcp](https://user-images.githubusercontent.com/112701413/192091532-16f77aea-a9df-43d8-b8a6-df5aedf01443.jpg)

  ## ipv4 address 
VLAN | ip address dhcp | excluded-address | host |
:----: | :----------: | :----: | :---: 
10 | 192.168.10.0/24 | 192.168.10.1-10; 192.168.10.254 | PC1 и PC3 

  ## ipv6 address 
VLAN | ip address dhcp | host |
:----: | :----------: | :----: |
20 | 2001:7BF:BAAD:A::1/64 | PC2 и PC4

## Настройка R1
1. Заходим в превилегированый режим **enable**
2. Переходим в режим конфигурации устройства **configure terminal**
3. Задаём имя для роутера **hostname R1**
>![1](https://user-images.githubusercontent.com/112701413/189698770-fa6f5f81-f215-4878-98aa-78ae22549d72.jpg)
4. Создаём сабинтерфейс для VLAN 10  **interface gigabitEthernet 0/0.10**
5. Задаем интефейсу работу с VLAN 10  **encapsulation dot1Q 10**
6. Задаем ip адрес и маску подсети  **ip address 192.168.10.1 255.255.255.0**
>![2](https://user-images.githubusercontent.com/112701413/189699752-132eb6bd-3e2d-4f52-ae22-88ab3d115c5e.jpg)
7. Записываем конфигурация во flash память **do wr**
8. Создаём сабинтерфейс для VLAN 20  **interface gigabitEthernet 0/0.20**
9. Задаем интефейсу работу с VLAN 20  **encapsulation dot1Q 20**
10. Задаем ipv6 адрес 
