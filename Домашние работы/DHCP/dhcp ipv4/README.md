# DHCP ipv4
 
  #### Настройка [R1](https://github.com/pekitel/OTUS-Network/blob/main/%D0%94%D0%BE%D0%BC%D0%B0%D1%88%D0%BD%D0%B8%D0%B5%20%D1%80%D0%B0%D0%B1%D0%BE%D1%82%D1%8B/DHCP/dhcp%20ipv4/README.md#%D0%BD%D0%B0%D1%81%D1%82%D1%80%D0%BE%D0%B9%D0%BA%D0%B0-r1-1)
  #### Настройка [R2](https://github.com/pekitel/OTUS-Network/tree/main/%D0%94%D0%BE%D0%BC%D0%B0%D1%88%D0%BD%D0%B8%D0%B5%20%D1%80%D0%B0%D0%B1%D0%BE%D1%82%D1%8B/DHCP/dhcp%20ipv4#%D0%BD%D0%B0%D1%81%D1%82%D1%80%D0%BE%D0%B9%D0%BA%D0%B0-r2-1)
  #### Настройка [Sw1](https://github.com/pekitel/OTUS-Network/blob/main/%D0%94%D0%BE%D0%BC%D0%B0%D1%88%D0%BD%D0%B8%D0%B5%20%D1%80%D0%B0%D0%B1%D0%BE%D1%82%D1%8B/DHCP/dhcp%20ipv4/README.md#%D0%BD%D0%B0%D1%81%D1%82%D1%80%D0%BE%D0%B9%D0%BA%D0%B0-sw1-1)
  #### Настройка [Sw2](https://github.com/pekitel/OTUS-Network/blob/main/%D0%94%D0%BE%D0%BC%D0%B0%D1%88%D0%BD%D0%B8%D0%B5%20%D1%80%D0%B0%D0%B1%D0%BE%D1%82%D1%8B/DHCP/dhcp%20ipv4/README.md#%D0%BD%D0%B0%D1%81%D1%82%D1%80%D0%BE%D0%B9%D0%BA%D0%B0-sw2-1)
  #### Проверка [ping](https://github.com/pekitel/OTUS-Network/blob/main/%D0%94%D0%BE%D0%BC%D0%B0%D1%88%D0%BD%D0%B8%D0%B5%20%D1%80%D0%B0%D0%B1%D0%BE%D1%82%D1%8B/DHCP/dhcp%20ipv4/README.md#%D0%BF%D1%80%D0%BE%D0%B2%D0%B5%D1%80%D0%B8%D0%BC-%D1%81%D0%B2%D1%8F%D0%B7%D0%BE%D0%BD%D0%BE%D1%81%D1%82%D1%8C-pc1-%D0%B8-pc2)
  
  ## Схема сети
  
![ipv4](https://user-images.githubusercontent.com/112701413/193915247-4c52f7e6-f0f8-4dd9-8c6e-0fc5e85cd5fc.jpg)

  ## ipv4 address 
host | int | VLAN | name | ip address | excluded-address | 
:----: | :---: | :---: | :----------: | :---: | :---: | 
R1 | Gi0/0 | | |10.0.0.1/30 | |no
| | Gi0/1.100 | 100 | User | 192.168.100.0/24 | 192.168.100.1-10; 192.168.100.254 |
| | Gi0/1.200 | 200 | MGMT |192.168.200.0/24 | | 
| | Gi0/1.1000 | 1000 | Native || |
R2 | Gi0/0 | | |10.0.0.2/30 | | 
| | Gi0/1.100 | 100 | User | 172.16.100.0/24 | 172.16.100.1-10; 172.16.100.254 | 
| | Gi0/1.200 | 200 | MGMT |172.16.200.0/24 | | 
| | Gi0/1.1000 | 1000 | Native | | | 
Sw1 | e0/0 | 200| MGMT | 192.168.200.10/24 | | 
|| e0/0 | 1000| Native | | | 
|| e0/1 | 100| User | | | 
Sw2 | e0/0 | 200| MGMT | 172.16.200.10/24 | | 
|| e0/0 | 1000| Native | | | 
|| e0/1 | 100| User | | | 
PC1 | eth0 | 100 | User | dhcp | | 
PC2 | eth0 | 100 | User | dhcp | | 

## Настройка R1
1. Заходим в превилегированый режим **enable**
2. Переходим в режим конфигурации устройства **configure terminal**
3. Задаём имя для роутера **hostname R1**
>![1](https://user-images.githubusercontent.com/112701413/189698770-fa6f5f81-f215-4878-98aa-78ae22549d72.jpg)
4. Перейдем в интерфейс Gi0/0 **interface gigabitEthernet 0/0**
5. Зададем ip адрес **ip address 10.0.0.1 255.255.255.252**
6. Включим интерфейс **no shutdown**
>![1](https://user-images.githubusercontent.com/112701413/193856079-d06ecdb4-4efc-46f3-a9b0-b2b811911b29.jpg)
7. Создадим сабинтерфейс для Native vlan **interface gigabitEthernet 0/1.1000**
8. Подпишим его **description Native**
9. Сделаем его нативным **encapsulation dot1Q 1000 native**
>![2](https://user-images.githubusercontent.com/112701413/193899081-5996f138-5fa1-4a42-ab13-0ca0d46a886d.jpg)
10. Создадим сабинтерфейс для vlan 100 **interface gigabitEthernet 0/1.100**
11. Подпишим его **description User**
12. Настроим его для работы с Vlan 100 **encapsulation dot1Q 100**
13. Настроим ip адрес для сабинтерфейс Gi0/1.100 **ip address 192.168.100.1 255.255.255.0**
14. Создадим сабинтерфейс для vlan 200 **interface gigabitEthernet 0/1.200**
15. Подпишим его **description MGMT**
16. Настроим его для работы с Vlan 200 **encapsulation dot1Q 200**
17. Настроим ip адрес для сабинтерфейс Gi0/1.200 **ip address 192.168.200.1 255.255.255.0**
18. И включим интерфейс Gi0/1 **no shutdown**
>![3](https://user-images.githubusercontent.com/112701413/193903817-0540e7ca-303f-4b0d-83dc-64d9b0eaa2b8.jpg)
19. Создадим POOL для Vlan 100 "User" **ip dhcp pool User**
20. Назначим адрес сети и маску **network 192.168.100.0 255.255.255.0**
21. Назначим адрес DNS сервера **dns-server 8.8.8.8**
22. Назначим адрес роутера по умолчанию **default-router 192.168.100.1**
>![4](https://user-images.githubusercontent.com/112701413/193906318-5641636b-16d9-4448-9435-8f7a91586208.jpg)
23. Создадим POOL для Vlan 100 на R2 "User_R2" **ip dhcp pool User_R2**
24. Назначим адрес сети и маску **network 172.16.100.0 255.255.255.0**
25. Назначим адрес DNS сервера **dns-server 8.8.8.8**
26. Назначим адрес роутера по умолчанию **default-router 172.16.100.1**
>![31](https://user-images.githubusercontent.com/112701413/195015783-27ba77fa-5282-4f53-9a8c-ab4a0dabe35c.jpg)
27. Так как мы знаем ip адрес соседнего роутера "R2" и адресацию его подситей то сразу настроим роутинг между ними
28. Скажем что подсеть с адресацией 172.16.100.0/24 находится за ip адресом "R2" **ip route 172.16.100.0 255.255.255.0 10.0.0.2**
29. Скажем что подсеть с адресацией 172.16.200.0/24 находится за ip адресом "R2" **ip route 172.16.200.0 255.255.255.0 10.0.0.2**
30. Записываем конфигурация во flash память **do wr**
>![5](https://user-images.githubusercontent.com/112701413/193908463-311efd15-897a-40e1-ac9c-bd38f6c0b235.jpg)
31. Исключим из выдачи по dhcp некоторые адреса **ip dhcp excluded-address 192.168.100.1 192.168.100.10**
32. Исключим из выдачи по dhcp ещё один адрес **ip dhcp excluded-address 192.168.100.254**
33. Записываем конфигурация во flash память **do wr**
>![13](https://user-images.githubusercontent.com/112701413/195016238-ea2bea01-8302-42a4-9f10-94f89eb93725.jpg)

## Настройка R2
1. Заходим в превилегированый режим **enable**
2. Переходим в режим конфигурации устройства **configure terminal**
3. Задаём имя для роутера **hostname R2**
>![6](https://user-images.githubusercontent.com/112701413/193917046-2349600d-cff7-467a-a2c7-3d84a0065a44.jpg)
4. Перейдем в интерфейс Gi0/0 **interface gigabitEthernet 0/0**
5. Зададем ip адрес **ip address 10.0.0.2 255.255.255.252**
6. Включим интерфейс **no shutdown**
>![7](https://user-images.githubusercontent.com/112701413/193917624-f47a8217-ed36-4b4f-a8e9-e85bbebe05a2.jpg)
7. Создадим сабинтерфейс для Native vlan **interface gigabitEthernet 0/1.1000**
8. Подпишим его **description Native**
9. Сделаем его нативным **encapsulation dot1Q 1000 native**
>![8](https://user-images.githubusercontent.com/112701413/193918088-1d0062e1-2cec-412a-bc08-d2965cbfece4.jpg)
10. Создадим сабинтерфейс для vlan 100 **interface gigabitEthernet 0/1.100**
11. Подпишим его **description User**
12. Настроим его для работы с Vlan 100 **encapsulation dot1Q 100**
13. Настроим ip адрес для сабинтерфейс Gi0/1.100 **ip address 172.16.100.1 255.255.255.0**
14. Создадим сабинтерфейс для vlan 200 **interface gigabitEthernet 0/1.200**
15. Подпишим его **description MGMT**
16. Настроим его для работы с Vlan 200 **encapsulation dot1Q 200**
17. Настроим ip адрес для сабинтерфейс Gi0/1.200 **ip address 172.16.200.1 255.255.255.0**
>![9](https://user-images.githubusercontent.com/112701413/194157991-312c7722-5281-4643-8bcd-6bf933eb1975.jpg)
18. Перейдем в интерфейс Gi0/1 **int gi0/1**
19. И включим интерфейс Gi0/1 **no shutdown**
>![9-1](https://user-images.githubusercontent.com/112701413/194158777-e45e5765-c4ea-494b-98b8-b92a0bc39ec1.jpg)
20. Так как мы знаем ip адрес соседнего роутера "R1" и адресацию его подситей то сразу настроим роутинг между ними
21. Скажем что подсеть с адресацией 192.168.100.0/24 находится за ip адресом "R1" **ip route 192.168.100.0 255.255.255.0 10.0.0.1**
22. Скажем что подсеть с адресацией 192.168.200.0/24 находится за ip адресом "R1" **ip route 192.168.200.0 255.255.255.0 10.0.0.1**
23. Записываем конфигурация во flash память **do wr**
>![11](https://user-images.githubusercontent.com/112701413/193921034-3f8ae2d0-e998-4d83-a6d8-ba33a321278a.jpg)
24. Перейдем в интерфейс Gi0/1.100 **int gi0/1.100**
25. Настроим получение ip адресов с dhcp сервера R1 **ip helper-address 10.0.0.1**
26. Проверим получил ли PC2 ip адрес **ip dhcp**
>![32](https://user-images.githubusercontent.com/112701413/195090559-12a23363-98d5-49da-9023-7e63d8146b66.jpg)

 
## Настройка Sw1
1. Заходим в превилегированый режим **enable**
2. Переходим в режим конфигурации устройства **configure terminal**
3. Задаём имя для роутера **hostname Sw1**
>![14](https://user-images.githubusercontent.com/112701413/193993547-ddce9d9f-1aaf-480a-8b6e-5883fcc6352d.jpg)
4. Создадим Vlan 100 для группы "User" **vlan 100**
5. Зададим имя для vlan **name User**
6. Аналогичным образом создадим vlan 200 "MGMT" и vlan 1000 "Native"
>![15](https://user-images.githubusercontent.com/112701413/194000690-e6496995-cc4e-4b52-95c5-3eb62365a6aa.jpg)
7. Перейдем к интерфейсу e0/0 **int e0/0**
8. Задаем интефейсу работу с VLAN  **switchport trunk encapsulation dot1q**
9. Назначим транковые VLANs **switchport trunk allowed vlan 100,200,1000**
10. Назначим VLAN 1000 нативный **switchport trunk native vlan 1000**
11. Переводим порт в режим trunk  **switchport mode trunk**
12. Выключаем передачу сообщений DTP  **switchport nonegotiate**
13. Подмишим порт что это *uplink* **description uplink**
14. Записываем конфигурация во flash память **do wr**
>![16](https://user-images.githubusercontent.com/112701413/194088341-1a4dd1dc-e04b-48d9-8a22-d5ece80bf0a2.jpg)
15. Перейдем в интерфейс *vlan 200* **int vlan 200**
16. Включим интерфейс **no shutdown**
17. Зададим ip адресс "т.к. для vlan 200 нет dhcp сервера" **ip address 192.168.200.10 255.255.255.0** 
18. Настроим для Sw1 шлюз по умолчанию **ip default-gateway 192.168.200.1**
>![17](https://user-images.githubusercontent.com/112701413/194086165-65658486-f75e-496d-a7c2-8d13082a4928.jpg)
19. Перейдем в интерфейс e0/1 **int e0/1**
20. Переводим порт в режим access **switchport mode access**
21. Настраиваем порт для работы в 100 vlan **switchport access vlan 100**
22. Записываем конфигурация во flash память **do wr**
>![18](https://user-images.githubusercontent.com/112701413/194090476-916bc0f4-c812-42d4-bc4e-383b351ff5c0.jpg)
23. Запросим ip адресс на PC1 **ip dhcp**
24. Посмотрим полную информацию на сетевом интерфейсе **show ip**

>![pc1v4](https://user-images.githubusercontent.com/112701413/194103008-adb7c614-98d7-47f0-88f3-e9038344697a.jpg)

Перейдем к R1 

23. Проверим сколько ip адресов выдалось **show ip dhcp pool**
>![19](https://user-images.githubusercontent.com/112701413/195091365-d99c1147-803a-4622-9c4c-3fdc190246e1.jpg)
24. Посмотрим какие ip адреса выдались и кому **show ip dhcp binding**
>![20](https://user-images.githubusercontent.com/112701413/195091583-b1cd8f0a-a704-453d-a7ff-a81b41ef0fef.jpg)
25. Видем что ip адрес *192.168.100.11* выдался PC1
26. Видем что ip адрес *172.16.100.11* выдался PC2

## Настройка Sw2
1. Заходим в превилегированый режим **enable**
2. Переходим в режим конфигурации устройства **configure terminal**
3. Задаём имя для роутера **hostname Sw2**
>![21](https://user-images.githubusercontent.com/112701413/194319757-16cb4815-4d09-47b1-8f39-32e304b037b2.jpg)
4. Создадим Vlan 100 для группы "User" **vlan 100**
5. Зададим имя для vlan **name User**
6. Аналогичным образом создадим vlan 200 "MGMT" и vlan 1000 "Native"
>![22](https://user-images.githubusercontent.com/112701413/194321006-92bd56be-1cad-43d5-a25e-67a1aa412a57.jpg)
7. Перейдем к интерфейсу e0/0 **int e0/0**
8. Задаем интефейсу работу с VLAN  **switchport trunk encapsulation dot1q**
9. Назначим транковые VLANs **switchport trunk allowed vlan 100,200,1000**
10. Назначим VLAN 1000 нативный **switchport trunk native vlan 1000**
11. Переводим порт в режим trunk  **switchport mode trunk**
12. Выключаем передачу сообщений DTP  **switchport nonegotiate**
13. Подмишим порт что это *uplink* **description uplink**
14. Записываем конфигурация во flash память **do wr**
>![23](https://user-images.githubusercontent.com/112701413/194322327-db6592d1-740a-4e10-a514-d8d6b1622037.jpg)
15. Перейдем в интерфейс *vlan 200* **int vlan 200**
16. Включим интерфейс **no shutdown**
17. Зададим ip адресс "т.к. для vlan 200 нет dhcp сервера" **ip address 172.16.200.10 255.255.255.0** 
18. Настроим для Sw2 шлюз по умолчанию **ip default-gateway 172.16.200.1**
>![24](https://user-images.githubusercontent.com/112701413/194323546-7b067c11-5276-4b1d-8f40-7b08b47498eb.jpg)
19. Перейдем в интерфейс e0/1 **int e0/1**
20. Переводим порт в режим access **switchport mode access**
21. Подпишим его **description PC2**
22. Настраиваем порт для работы в 100 vlan **switchport access vlan 100**
23. Записываем конфигурация во flash память **do wr**
>![25](https://user-images.githubusercontent.com/112701413/194324500-4e798be1-6533-484f-9b91-038fedf7556c.jpg)

## Проверим связоность PC1 и PC2

1. С PC1 запустим icmp запросы на ip адрес PC2 **ping 172.16.100.11**
>![29](https://user-images.githubusercontent.com/112701413/194331712-76eeba80-b236-40ad-bd6d-ded43750562d.jpg)
2. С PC2 запустим icmp запросы на ip адрес PC2 **ping 192.168.100.11**
>![30](https://user-images.githubusercontent.com/112701413/194333355-14f25e9c-2511-4a75-a102-ce9bdbfc617a.jpg)
