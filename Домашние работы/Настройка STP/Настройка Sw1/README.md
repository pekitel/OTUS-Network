## Настройка Sw1
1. Заходим в превилегированый режим **enable**
2. Переходим в режим конфигурации **configure terminal**
3. Задаём имя для коммутатора **hostname Sw1**
4. Создаём VLAN 2  **vlan 2** 
5. Аналогичным образом создаём и VLANs 10, 20 ,30 и 40
6. Включаем протокол STP **spanning-tree mode rapid-pvst**
7. Настраивае приоритет для VLANs 10,20 **spanning-tree vlan 10,20 priority 4096** 
> ![111](https://user-images.githubusercontent.com/112701413/189530073-fe29e774-c55d-4927-958f-5db4d9182192.jpg)
8. ***Настраиваем trunk порты***
9. Переходим в интерфейсы Gi0/1 и Gi0/2 **interface range gigabitEthernet 0/1-2**
10. Задаем интефейсу работу с VLAN **switchport trunk encapsulation dot1q**
11. Назначим транковые VLANs **switchport trunk allowed vlan 2,10,20,30**
12. Назначим VLAN 2 нативный **switchport trunk native vlan 2**
13. Переводим порт в режим **trunk switchport mode trunk**
14. Выключаем передачу сообщений DTP **switchport nonegotiate**
15. Записываем конфигурация во flash память **do wr**
> ![123](https://user-images.githubusercontent.com/112701413/189531124-1e73940b-52a8-4c21-b5b0-dc485f0aefdf.jpg)
16. ***Настраиваем access порты***
17. Переходим в интерфейс Fa0/10 **interface fastEthernet 0/10**
18. Переводим порт в режим access **switchport mode access**
19. Настраиваем порт для работы в 40 vlan **switchport access vlan 40**
20. Выключаем передачу сообщений DTP  **switchport nonegotiate**
21. Включаем *portfast* **spanning-tree portfast trunk**
22. Отключаем получения BPDU пакетов **spanning-tree bpduguard enable**
23. Записываем конфигурация во flash память **do wr**
> ![321](https://user-images.githubusercontent.com/112701413/189531252-07590096-f1b4-4474-9432-e44acf9c8065.jpg)
24. Аналогичным образом (п17-23) настраиваем порт для VLAN 30
25. Переходим в интерфейсы Fa0/1 и Fa0/2 **interface range fastEthernet 0/1-2**
26. Переводим порты в режим access **switchport mode access**
27. Настраиваем порты для работы в 10 vlan **switchport access vlan 10**
28. Выключаем передачу сообщений DTP  **switchport nonegotiate**
29. Видим что порт Fa0/2 перешол в режим *backup* чтобы предотвратить петлю
> ![222](https://user-images.githubusercontent.com/112701413/189533072-af367c05-c77d-49c0-83a9-c8586accf03c.jpg)
