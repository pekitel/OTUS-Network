# DHCP
  1. Настройка DHCP ipv4
  2. Настройка DHCP ipv6
  
  ## Схема сети
  
![dhcp](https://user-images.githubusercontent.com/112701413/193837728-b23ae5df-c30f-409e-9d04-511a8697b7ea.jpg)

  ## ipv4 address 
host | int | VLAN | name | ip address | excluded-address | DHCP |
:----: | :---: | :---: | :----------: | :----: | :---: | :---: 
R1 | Gi0/0 | | |10.0.0.1/30 | |no
| | Gi0/1.100 | 100 | User | 192.168.100.0/24 | 192.168.100.1-10; 192.168.100.254 |  yes
| | Gi0/1.200 | 200 | MGMT |192.168.200.0/24 | |no
| | Gi0/1.1000 | 1000 | Native | | |no
R2 | Gi0/0 | | |10.0.0.2/30 | |no
| | Gi0/1.100 | 100 | User | 172.16.100.0/24 | 172.16.100.1-10; 172.16.100.254 |  yes
| | Gi0/1.200 | 200 | MGMT |172.16.200.0/24 | |no
| | Gi0/1.1000 | 1000 | Native | | |no
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
18. Задаем диапазон ipv6 адресов для выдачи хостам **address prefix 2001:7BF:BAAD:A::/64**
19. Задаем доменное имя для этой подсети **domain-name lab2.ru**
>![26](https://user-images.githubusercontent.com/112701413/192095896-b27b8b13-99c9-4020-a445-508baec80b22.jpg)
20. Включаем протакол ipv6 **ipv6 unicast-routing**
>![28](https://user-images.githubusercontent.com/112701413/192096700-1b6d2838-bb7a-431f-9569-de0b7f573ebd.jpg)
21. Включаем интерфейс *Gi0/0* **no shutdown**
>![29](https://user-images.githubusercontent.com/112701413/192096695-912ee851-117b-4e97-a986-ea327bf816e3.jpg)
22. Также создаем сабинтерфейс для VLAN 2 и делаем его нативным **encapsulation dot1Q 2 native**
23. Записываем конфигурация во flash память **do wr**
>![2](https://user-images.githubusercontent.com/112701413/192096835-d5025c26-10a9-4c75-ab2c-1ccb102d3da3.jpg)

## Настройка Sw1
1. Заходим в превилегированый режим **enable**
2. Переходим в режим конфигурации устройства **configure terminal**
3. Задаём имя для роутера **hostname Sw1**
>![9](https://user-images.githubusercontent.com/112701413/192097353-0748eae8-0f77-4dcb-85be-be8f1a4dce24.jpg)
4. Создаем Vlan 2 **vlan 2**
5. Аналогичным образом создаём и VLANs 10, 20
>![10](https://user-images.githubusercontent.com/112701413/192097430-b702cbe6-74be-4dfa-ab15-0bb7901ba060.jpg)
6. ***Настраиваем trunk порты***
7. Переходим в интерфейсы Gi0/0 и Gi0/1 **interface range gigabitEthernet 0/0-2**
8. Задаем интефейсам работу с VLAN  **switchport trunk encapsulation dot1q**
9. Назначим транковые VLANs **switchport trunk allowed vlan 2,10,20**
>![11](https://user-images.githubusercontent.com/112701413/192097590-bea80ce9-6e4d-48ba-8c36-1f6eb696a4be.jpg)
10. Назначим VLAN 2 нативный **switchport trunk native vlan 2**
11. Переводим порт в режим trunk  **switchport mode trunk**
12. Выключаем передачу сообщений DTP  **switchport nonegotiate**
>![12](https://user-images.githubusercontent.com/112701413/192097630-e6ccff96-5732-4a64-8851-0c6d1d58581c.jpg)
13. ***Настраиваем access порты***
14. Переходим в интерфейс Gi0/2 **interface GigabitEthernet0/2**
15. Переводим порт в режим access **switchport mode access**
16. Настраиваем порт для работы в 10 vlan **switchport access vlan 10**
>![14](https://user-images.githubusercontent.com/112701413/192097741-5be59c73-0c24-4502-8728-b05134e3a588.jpg)
17. Выключаем передачу сообщений DTP  **switchport nonegotiate**
18. Включаем *portfast* **spanning-tree portfast**
19. Отключаем получения BPDU пакетов **spanning-tree bpduguard enable**
20. Записываем конфигурация во flash память **do wr**
>![15](https://user-images.githubusercontent.com/112701413/192098017-f7337f01-719c-4905-a2c8-9ed62271af49.jpg)
21. Аналогичным образом настраиваем порт Gi0/3 для Vlan 20
## Настройка Sw2
1. Заходим в превилегированый режим **enable**
2. Переходим в режим конфигурации устройства **configure terminal**
3. Задаём имя для роутера **hostname Sw2**
>![17](https://user-images.githubusercontent.com/112701413/192098473-90d18850-6951-43cd-8d0c-f04a2aca9105.jpg)
4. Создаем Vlan 2 **vlan 2**
5. Аналогичным образом создаём и VLANs 10, 20
>![18](https://user-images.githubusercontent.com/112701413/192098496-7ce9d548-20cb-4366-851e-a31562740566.jpg)
6. ***Настраиваем trunk порт***
7. Переходим в интерфейс Gi0/0 **interface gigabitEthernet 0/0**
8. Задаем интефейсам работу с VLAN  **switchport trunk encapsulation dot1q**
9. Назначим транковые VLANs **switchport trunk allowed vlan 2,10,20**
>![19](https://user-images.githubusercontent.com/112701413/192098603-f41b114f-e10e-4edb-8a2e-de18a84c8630.jpg)
10. Назначим VLAN 2 нативный **switchport trunk native vlan 2**
11. Переводим порт в режим trunk  **switchport mode trunk**
12. Выключаем передачу сообщений DTP  **switchport nonegotiate**
>![20](https://user-images.githubusercontent.com/112701413/192098682-237b6ab9-2013-4e8b-867f-7068c9dd23cf.jpg)
13. ***Настраиваем access порты***
14. Переходим в интерфейс Gi0/1 **interface GigabitEthernet0/1**
15. Переводим порт в режим access **switchport mode access**
>![21](https://user-images.githubusercontent.com/112701413/192098784-9398815f-e66c-430f-9ec1-74d920017b4d.jpg)
16. Настраиваем порт для работы в 10 vlan **switchport access vlan 10**
>![22](https://user-images.githubusercontent.com/112701413/192098810-62c39596-84a9-458e-9938-01de7b6b8487.jpg)
17. Выключаем передачу сообщений DTP  **switchport nonegotiate**
18. Включаем *portfast* **spanning-tree portfast**
19. Отключаем получения BPDU пакетов **spanning-tree bpduguard enable**
>![23](https://user-images.githubusercontent.com/112701413/192098903-7f8c06b1-5113-4995-8f55-192abcb79548.jpg)
20. Аналогичным образом настраиваем порт Gi0/2 для Vlan 20
21. ***Проверяем выдаются ли адреса в vlan 10 и vlan 20***
22. PC1 должен получить адрес ipv4 **ip dhcp**
>![30](https://user-images.githubusercontent.com/112701413/192099405-8e321707-7247-4ae6-ae05-71029f6d32cd.jpg)
23. Проверяем настройки PC1 **show ip**
>![31](https://user-images.githubusercontent.com/112701413/192099573-508a96cf-4815-4318-85b6-36c3fa9a8156.jpg)
24. Видим что PC1 получил ip адрес и dns
25. PC2 должен получить адрес ipv6 **ip auto**
>![32](https://user-images.githubusercontent.com/112701413/192099634-04e54aea-9b92-4d54-bbcd-08fd458d9eac.jpg)
26. Проверяем настройки PC2 **show ipv6**
> ![33](https://user-images.githubusercontent.com/112701413/192100820-3dd3aec5-1ec9-4b21-86f8-06ab23678f71.jpg)
27. Видим что PC2 получил ipv6 адрес где первые 64 бита это префикс сети ipv6 а вторые 64 бита это индификатор интерфейса. 
28. Он генеригуется ( процедура EUI-64 ) таким образом что подставляется mac-address устройства и в середину добавляется ff:fe , а первый байт изменяется. 
