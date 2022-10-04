# DHCP ipv4
 
  #### Настройка [R1](https://github.com/pekitel/OTUS-Network/blob/main/%D0%94%D0%BE%D0%BC%D0%B0%D1%88%D0%BD%D0%B8%D0%B5%20%D1%80%D0%B0%D0%B1%D0%BE%D1%82%D1%8B/DHCP/dhcp%20ipv4/README.md#%D0%BD%D0%B0%D1%81%D1%82%D1%80%D0%BE%D0%B9%D0%BA%D0%B0-r1-1)
  #### Настройка [R2](https://github.com/pekitel/OTUS-Network/tree/main/%D0%94%D0%BE%D0%BC%D0%B0%D1%88%D0%BD%D0%B8%D0%B5%20%D1%80%D0%B0%D0%B1%D0%BE%D1%82%D1%8B/DHCP/dhcp%20ipv4#%D0%BD%D0%B0%D1%81%D1%82%D1%80%D0%BE%D0%B9%D0%BA%D0%B0-r2-1)
  
  ## Схема сети
  
![ipv4](https://user-images.githubusercontent.com/112701413/193915247-4c52f7e6-f0f8-4dd9-8c6e-0fc5e85cd5fc.jpg)

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
|| e0/0 | 1000| Native | | | no
|| e0/1 | 100| User | | | no
Sw2 | e0/0 | 200| MGMT | 172.16.200.10/24 | | no
|| e0/0 | 1000| Native | | | no
|| e0/1 | 100| User | | | no
PC1 | eth0 | 100 | User | | | yes
PC2 | eth0 | 100 | User | | | yes

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
23. Так как мы знаем ip адрес соседнего роутера "R2" и адресацию его подситей то сразу настроим роутинг между ними
24. Скажем что подсеть с адресацией 172.16.100.0/24 находится за ip адресом "R2" **ip route 172.16.100.0 255.255.255.0 10.0.0.2**
25. Скажем что подсеть с адресацией 172.16.200.0/24 находится за ip адресом "R2" **ip route 172.16.200.0 255.255.255.0 10.0.0.2**
26. Записываем конфигурация во flash память **do wr**
>![5](https://user-images.githubusercontent.com/112701413/193908463-311efd15-897a-40e1-ac9c-bd38f6c0b235.jpg)

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
18. И включим интерфейс Gi0/1 **no shutdown**
>![9](https://user-images.githubusercontent.com/112701413/193918901-2e8c0b4d-0a92-4e9a-8dae-5a3c22d41e13.jpg)

