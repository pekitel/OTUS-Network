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
7. Настраиваем *DHCP POOL* **ip dhcp pool POOL_ipv4**
8. Задаем ip адрес сети и маску **network 192.168.10.0 255.255.255.0**
9. Задаем ip адрес шлюза **default-router 192.168.10.1**
10. Задаем ip адрес *DNS* сервера **dns-server 8.8.8.8**
>![dhcp_pool_ipv4](https://user-images.githubusercontent.com/112701413/192094611-638d45b0-2de5-4806-a7bf-f006a2444ec1.jpg)
11. Исключаем диапазон ip адресов которые не должны выдоваться по *dhcp* **ip dhcp excluded-address 192.168.10.1 192.168.10.10**
12. И также исключим последний ip адрес **ip dhcp excluded-address 192.168.10.254**
>![8](https://user-images.githubusercontent.com/112701413/192094228-cdf1a8b5-b15b-4879-b008-3a5891f01d95.jpg)
13. Записываем конфигурация во flash память **do wr**
14. Создаём сабинтерфейс для VLAN 20  **interface gigabitEthernet 0/0.20**
15. Задаем интефейсу работу с VLAN 20  **encapsulation dot1Q 20**
>![24](https://user-images.githubusercontent.com/112701413/192095198-c101d278-0de9-4c27-8d54-d38fb1652613.jpg)
16. Задаем ipv6 адрес **ipv6 address 2001:7BF:BAAD:A::1/64**
>![25](https://user-images.githubusercontent.com/112701413/192095154-e990653f-a74d-4539-be95-e2d6c3bdc852.jpg)
17. Настраиваем *DHCP POOL* **ip dhcp pool POOL_ipv6**
18. Задаем диапазон ipv6 адресов для выдачи хостам **address prefix 2001:7BF:BAAD:A::/64
19. Задаем доменное имя для этой подсети **domain-name lab2.ru
>![26](https://user-images.githubusercontent.com/112701413/192095896-b27b8b13-99c9-4020-a445-508baec80b22.jpg)
20. Включаем протакол ipv6 **ipv6 unicast-routing**
>![28](https://user-images.githubusercontent.com/112701413/192096700-1b6d2838-bb7a-431f-9569-de0b7f573ebd.jpg)
21. Включаем интерфейс *Gi0/0* **no shutdown**
>![29](https://user-images.githubusercontent.com/112701413/192096695-912ee851-117b-4e97-a986-ea327bf816e3.jpg)
22. Также создаем сабинтерфейс для VLAN 2 и делаем его нативным **encapsulation dot1Q 2 native**
23. Записываем конфигурация во flash память **do wr**
>![2](https://user-images.githubusercontent.com/112701413/192096835-d5025c26-10a9-4c75-ab2c-1ccb102d3da3.jpg)

## Настройка Sw1
