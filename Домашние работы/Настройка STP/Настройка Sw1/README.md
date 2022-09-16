## Настройка Sw1
1. Заходим в превилегированый режим **enable**
2. Переходим в режим конфигурации **configure terminal**
3. Задаём имя для коммутатора **hostname Sw1**
>![4](https://user-images.githubusercontent.com/112701413/189899271-123d4305-6359-40c9-a3de-f6533148938a.jpg)
4. Создаём VLAN 2  **vlan 2** 
5. Аналогичным образом создаём и VLANs 10, 20 ,30 и 40
>![5](https://user-images.githubusercontent.com/112701413/189900167-498707a8-d0ad-40b3-b6c9-52595e99f4c3.jpg)
6. Включаем протокол RSTP **spanning-tree mode rapid-pvst**
>![6](https://user-images.githubusercontent.com/112701413/190339033-3264d734-634b-4769-9d87-e37363c320d3.jpg)
7. Настраивае приоритет для VLANs 10,20 **spanning-tree vlan 10,20 priority 4096** 
>![7](https://user-images.githubusercontent.com/112701413/190339427-331fe1da-5f3b-4ecf-be32-9a01ca2d0448.jpg)
8. ***Настраиваем trunk порты***
9. Настраиваем интерфейс Fa/0/24 смотрящий в сторону R1 **interface fastEthernet 0/24**
10. Назначим транковые VLANs **switchport trunk allowed vlan 2,10,20,30,40**
11. Назначим VLAN 2 нативный **switchport trunk native vlan 2**
12. Переводим порт в режим trunk **switchport mode trunk**
13. Выключаем передачу сообщений DTP **switchport nonegotiate**
>![14](https://user-images.githubusercontent.com/112701413/190673457-2d64c237-3798-41f1-b691-6902178fcf7b.jpg)
14. Переходим в интерфейсы Gi0/1 и Gi0/2 **interface range gigabitEthernet 0/1-2**
15. Назначим транковые VLANs **switchport trunk allowed vlan 2,10,20,30,40**
16. Назначим VLAN 2 нативный **switchport trunk native vlan 2**
17. Переводим порт в режим trunk **switchport mode trunk**
18. Выключаем передачу сообщений DTP **switchport nonegotiate**
>![8](https://user-images.githubusercontent.com/112701413/190342233-86a23351-0280-4055-b60e-4b3e21de487e.jpg)
19. Записываем конфигурация во flash память **do wr**
20. Переходим в настройку порта Gi0/1 **interface gigabitEthernet 0/1**
21. Установливаем *Cost-20* для VLAN 10 **spanning-tree vlan 10 cost 20**
22. Установливаем *Cost-50* для VLAN 20 **spanning-tree vlan 20 cost 50**
23. Аналогичным образом настраиваем *Cost* для порта Gi0/2
24. Переходим в настройку порта Gi0/2 **interface gigabitEthernet 0/2**
25. Установливаем *Cost-50* для VLAN 10 **spanning-tree vlan 10 cost 50**
26. Установливаем *Cost-20* для VLAN 20 **spanning-tree vlan 20 cost 20**
27. Записываем конфигурация во flash память **do wr**

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
