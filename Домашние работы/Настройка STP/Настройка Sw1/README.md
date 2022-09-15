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
9. Переходим в интерфейсы Gi0/1 и Gi0/2 **interface range gigabitEthernet 0/1-2**
10. Задаем интефейсу работу с VLAN **switchport trunk encapsulation dot1q**
11. Назначим транковые VLANs **switchport trunk allowed vlan add 2,10,20,30**
12. Назначим VLAN 2 нативный **switchport trunk native vlan 2**
13. Переводим порт в режим trunk **switchport mode trunk**
14. Выключаем передачу сообщений DTP **switchport nonegotiate**
>![8](https://user-images.githubusercontent.com/112701413/190342233-86a23351-0280-4055-b60e-4b3e21de487e.jpg)
15. Записываем конфигурация во flash память **do wr**
> ![123](https://user-images.githubusercontent.com/112701413/189531124-1e73940b-52a8-4c21-b5b0-dc485f0aefdf.jpg)
16. Переходим в настройку порта Gi0/1 **interface gigabitEthernet 0/1**
17. Установливаем *Cost-20* для VLAN 10 **spanning-tree vlan 10 cost 20**
18. Установливаем *Cost-50* для VLAN 20 **spanning-tree vlan 20 cost 50**
19. Аналогичным образом настраиваем *Cost* для порта Gi0/2
20. Переходим в настройку порта Gi0/2 **interface gigabitEthernet 0/2**
21. Установливаем *Cost-50* для VLAN 10 **spanning-tree vlan 10 cost 50**
22. Установливаем *Cost-20* для VLAN 20 **spanning-tree vlan 20 cost 20**
23. Записываем конфигурация во flash память **do wr**

>![10](https://user-images.githubusercontent.com/112701413/190414253-b883c438-d498-4e65-b582-4dd0a9918b7f.jpg)

Таким образом трафик для VLAN 10 пойдет через Gi0/1 ,а трафик для VLAN 20 пойдет через Gi0/2

24. Проверяем конфигурацию командой **show running-config**
>![11](https://user-images.githubusercontent.com/112701413/190416815-e480e673-c133-436b-9aca-42257f25dd5d.jpg)

