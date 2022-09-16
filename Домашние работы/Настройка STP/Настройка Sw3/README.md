## Настройка Sw3
1. Заходим в превилегированый режим **enable**
2. Переходим в режим конфигурации **configure terminal**
3. Задаём имя для коммутатора **hostname Sw3**
>![21](https://user-images.githubusercontent.com/112701413/190704021-ca207155-ab04-4b96-a6ed-397141042829.jpg)
4. Создаём VLAN 2  **vlan 2** 
5. Аналогичным образом создаём и VLANs 10, 20 ,30 и 40
>![22](https://user-images.githubusercontent.com/112701413/190704309-6d06ad2e-ab3c-444c-beb9-5ae0c50a941e.jpg)
6. Включаем протокол RSTP **spanning-tree mode rapid-pvst**
>![23](https://user-images.githubusercontent.com/112701413/190704756-78ca434f-542a-4d39-ace1-8cf939d474e8.jpg)
7. Настраивае приоритет для VLANs 10,20 **spanning-tree vlan 30,40 priority 4096** 
>![24](https://user-images.githubusercontent.com/112701413/190705250-478609f1-f286-4a87-b95a-e80d8055ae03.jpg)
8. ***Настраиваем trunk порты***
9. Переходим в интерфейсы Gi0/1 и Gi0/2 **interface range gigabitEthernet 0/1-2**
10. Назначим транковые VLANs **switchport trunk allowed vlan 2,10,20,30**
11. Назначим VLAN 2 нативный **switchport trunk native vlan 2**
12. Переводим порт в режим trunk **switchport mode trunk**
13. Выключаем передачу сообщений DTP **switchport nonegotiate**
>![25](https://user-images.githubusercontent.com/112701413/190706226-6f08aab7-a575-47bf-a17a-36bee3d29f78.jpg)
14. Записываем конфигурация во flash память **do wr**
15. Переходим в настройку порта Gi0/1 **interface gigabitEthernet 0/1**
16. Установливаем *Cost-50* для VLAN 30 **spanning-tree vlan 30 cost 50**
17. Установливаем *Cost-20* для VLAN 40 **spanning-tree vlan 40 cost 20**
18. Аналогичным образом настраиваем *Cost* для порта Gi0/2
19. Переходим в настройку порта Gi0/2 **interface gigabitEthernet 0/2**
20. Установливаем *Cost-50* для VLAN 30 **spanning-tree vlan 30 cost 20**
21. Установливаем *Cost-20* для VLAN 40 **spanning-tree vlan 40 cost 50**
22. Записываем конфигурация во flash память **do wr**
>![26](https://user-images.githubusercontent.com/112701413/190712524-c552e0d1-dbe9-4f4b-88c1-c10cd518a656.jpg)

Таким образом трафик для VLAN 40 пойдет через Gi0/1 ,а трафик для VLAN 30 пойдет через Gi0/2

28. Проверяем конфигурацию командой **show running-config**
>![27](https://user-images.githubusercontent.com/112701413/190712817-531f2888-20d3-403b-9d31-c298a88087bb.jpg)
29. Посмотрим настройки spanning-tree для VLANs 30,40 **show spanning-tree vlan 30,40**
30. Видим что Sw3 стал корневым для VLANs 30,40
>![28](https://user-images.githubusercontent.com/112701413/190713334-a5803f9e-8091-4ce8-be70-ca52fd8ae91a.jpg)
31. ***Настраиваем access порты***
32. Переходим в интерфейсы Fa0/1 и Fa0/2 **interface range fastEthernet 0/1-2**
33. Переводим порты в режим access **switchport mode access**
34. Настраиваем порты для работы в 10 vlan **switchport access vlan 10**
>![29](https://user-images.githubusercontent.com/112701413/190713824-063c9aa1-3e5d-4e4e-9105-013c0e05b504.jpg)
35. Записываем конфигурация во flash память **do wr**
36. Посмотрим режим портов spanning-tree для VLANs 10,20
>![30](https://user-images.githubusercontent.com/112701413/190715845-5e8352e0-1054-496c-b994-c16ccab1bdd8.jpg)
37. Видим что порты Fa0/1 и Fa0/2 перешли в режим *Designated*
38. Порты Gi0/1 и Gi0/2 перешли в режим *alternative* (для предотвращение петли)


