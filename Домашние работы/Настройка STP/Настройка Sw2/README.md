## Настройка Sw2
1. Заходим в превилегированый режим **enable**
2. Переходим в режим конфигурации **configure terminal**
3. Задаём имя для коммутатора **hostname Sw2**
4. Создаём VLAN 2  **vlan 2** 
5. Аналогичным образом создаём и VLANs 10, 20 ,30 и 40
6. Включаем протокол STP **spanning-tree mode rapid-pvst**
7. Настраивае приоритет для VLANs 30,40 **spanning-tree vlan 30,40 priority 4096**
> ![333](https://user-images.githubusercontent.com/112701413/189541418-718bafad-347d-41a6-ab49-f4f1fe12b449.jpg)
8. ***Настраиваем trunk порты***
9. Переходим в интерфейсы Gi0/1 и Gi0/2 **interface range gigabitEthernet 0/1-2**
10. Задаем интефейсу работу с VLAN **switchport trunk encapsulation dot1q**
11. Назначим транковые VLANs **switchport trunk allowed vlan 2,10,20,30**
12. Назначим VLAN 2 нативный **switchport trunk native vlan 2**
13. Переводим порт в режим **trunk switchport mode trunk**
14. Выключаем передачу сообщений DTP **switchport nonegotiate**
15. Записываем конфигурация во flash память **do wr**
> ![123](https://user-images.githubusercontent.com/112701413/189531124-1e73940b-52a8-4c21-b5b0-dc485f0aefdf.jpg)

**Видим что порты *Gi0/1* и *Gi0/2* перешли в режим *Designated***

> ![111](https://user-images.githubusercontent.com/112701413/189541225-7b8ead3c-0bbf-423f-b440-113b132b6bd6.jpg)
16. ***Настраиваем access порты***
17. Переходим в интерфейс Fa0/10 **interface fastEthernet 0/10**
18. Переводим порт в режим access **switchport mode access**
19. Настраиваем порт для работы в 10 vlan **switchport access vlan 10**
20. Выключаем передачу сообщений DTP  **switchport nonegotiate**
21. Включаем *portfast* **spanning-tree portfast trunk**
22. Отключаем получения BPDU пакетов **spanning-tree bpduguard enable**
23. Записываем конфигурация во flash память **do wr**
> ![sw2-10](https://user-images.githubusercontent.com/112701413/189541808-1b70df40-b099-4602-a244-32fb82b97e02.jpg)
24. Аналогичным образом (п17-23) настраиваем порт Fa0/11 для VLAN 20
25. Переходим в интерфейсы Fa0/1 и Fa0/2 **interface range fastEthernet 0/1-2**
26. Переводим порты в режим access **switchport mode access**
27. Настраиваем порты для работы в 30 vlan **switchport access vlan 30**
28. Выключаем передачу сообщений DTP  **switchport nonegotiate**

**Видим что порты *Fa0/1* и *Fa0/2* перешли в режим *Designated*** 

> ![fa1-2](https://user-images.githubusercontent.com/112701413/189542165-0ca6e28c-bc01-43e0-909b-d272934a4973.jpg)
29. Записываем конфигурация во flash память **do wr**
