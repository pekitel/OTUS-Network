## Настройка Sw1
1. Заходим в превилегированый режим **enable**
2. Переходим в режим конфигурации **configure terminal**
3. Задаём имя для коммутатора **hostname Sw1**
4. Создаём VLAN 2  **vlan 2** 
5. Аналогичным образом создаём и VLANs 10, 20 ,30 и 40
6. Включаем протокол STP **spanning-tree mode rapid-pvst**
7. Настраивае приоритет для VLANs 10,20 **spanning-tree vlan 10,20 priority 4096**
8. ***Настраиваем trunk порты***
9. Переходим в интерфейс Gi0/0 interface GigabitEthernet0/0
10. Задаем интефейсу работу с VLAN switchport trunk encapsulation dot1q
11. Назначим транковые VLANs switchport trunk allowed vlan 2,10,20,30
12. Назначим VLAN 2 нативный switchport trunk native vlan 2
13. Переводим порт в режим trunk switchport mode trunk
14. Выключаем передачу сообщений DTP switchport nonegotiate
15. Записываем конфигурация во flash память do wr
