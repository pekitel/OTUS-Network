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
16. Установливаем *Cost-20* для VLAN 30 **spanning-tree vlan 10 cost 20**
17. Установливаем *Cost-50* для VLAN 40 **spanning-tree vlan 20 cost 50**








18. Аналогичным образом настраиваем *Cost* для порта Gi0/2
19. Переходим в настройку порта Gi0/2 **interface gigabitEthernet 0/2**
20. Установливаем *Cost-50* для VLAN 10 **spanning-tree vlan 10 cost 50**
21. Установливаем *Cost-20* для VLAN 20 **spanning-tree vlan 20 cost 20**
22. Записываем конфигурация во flash память **do wr**

>![10](https://user-images.githubusercontent.com/112701413/190414253-b883c438-d498-4e65-b582-4dd0a9918b7f.jpg)

Таким образом трафик для VLAN 10 пойдет через Gi0/1 ,а трафик для VLAN 20 пойдет через Gi0/2

28. Проверяем конфигурацию командой **show running-config**
>![11](https://user-images.githubusercontent.com/112701413/190674725-b15c673c-dfdb-43ef-b66a-c52351d3ff8c.jpg)


29. Посмотрим настройки spanning-tree для VLANs 10,20 **show spanning-tree vlan 10,20**
30. Видим что Sw1 стал корневым для VLANs 10,20
>![9](https://user-images.githubusercontent.com/112701413/190575360-a7b9cc0d-86df-4ec6-9e87-afe7e16581a3.jpg)
31. ***Настраиваем access порты***
32. Переходим в интерфейс Fa0/1 **interface fastEthernet 0/1**
33. Переводим порт в режим access **switchport mode access**
34. Настраиваем порт для работы в 10 vlan **switchport access vlan 10**
>![12](https://user-images.githubusercontent.com/112701413/190576031-0a8381e9-614c-4a24-8516-87c633672e82.jpg)
35. Выключаем передачу сообщений DTP  **switchport nonegotiate**
36. Включаем *portfast* **spanning-tree portfast**
37. Отключаем получения BPDU пакетов **spanning-tree bpduguard enable**
38. Записываем конфигурация во flash память **do wr**
>![13](https://user-images.githubusercontent.com/112701413/190577047-d86cae5a-a580-4f03-a7af-e785e39e49d2.jpg)
39. Аналогичным образом настраиваем порт fa0/2 для Vlan 30
40. Записываем конфигурация во flash память **do wr**

