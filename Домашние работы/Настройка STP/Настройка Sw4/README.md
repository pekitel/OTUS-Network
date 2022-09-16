1. Заходим в превилегированый режим **enable**
2. Переходим в режим конфигурации **configure terminal**
3. Задаём имя для коммутатора **hostname Sw4**
>![35](https://user-images.githubusercontent.com/112701413/190747781-364ca577-2160-45f8-876b-33bcc9af2b0c.jpg)
4. Создаём VLAN 2  **vlan 2**
5. Аналогичным образом создаём и VLANs 10, 20 ,30 и 40
> ![36](https://user-images.githubusercontent.com/112701413/190748850-311fbb10-2d15-401d-aa12-4407cca33cf3.jpg)
6. Включаем протокол RSTP **spanning-tree mode rapid-pvst**
>![37](https://user-images.githubusercontent.com/112701413/190750754-4024ea15-61c8-4d49-b590-16c643a4f469.jpg)
7. ***Настраиваем trunk порты***
8. Переходим в интерфейсы Gi0/1 и Gi0/2 **interface range gigabitEthernet 0/1-2**
9. Назначим транковые VLANs **switchport trunk allowed vlan 2,10,20,30,40**
10. Назначим VLAN 2 нативный **switchport trunk native vlan 2**
11. Переводим порт в режим trunk **switchport mode trunk**
12. Выключаем передачу сообщений DTP **switchport nonegotiate**
>![38](https://user-images.githubusercontent.com/112701413/190756212-ccea3f57-41e3-477b-9914-450479dd3242.jpg)
13. Записываем конфигурация во flash память **do wr**
14. ***Настраиваем access порты***
15. Переходим в интерфейсы Fa0/1 и Fa0/2 **interface range fastEthernet 0/1-2**
16. Переводим порты в режим access **switchport mode access**
17. Настраиваем порты для работы в 20 vlan **switchport access vlan 20**
>![39](https://user-images.githubusercontent.com/112701413/190769732-1609b543-fa4a-4ee5-89d4-fbfaf6b0e44c.jpg)
18. Посмотрим режим портов Fa0/1 и Fa0/2 spanning-tree для VLANs 20
>![40](https://user-images.githubusercontent.com/112701413/190782820-5479234b-6cdb-4360-98d1-40b34ea45417.jpg)
