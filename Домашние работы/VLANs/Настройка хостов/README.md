## Настройка R1
1. Заходим в превелегированый режим **enable**
2. Переходим в режим глобальной конфигурации **configure terminal**
3. Создаём сабинтерфейс для VLAN 10  **interface gigabitEthernet 0/0.10**
4. Задаем интефейсу работу с VLAN 10  **encapsulation dot1Q 10**
5. Задаем ip адрес и маску подсети  **ip address 192.168.10.1 255.255.255.0**
6. Аналогичным образом создаём и настраиваем сабинтерфейсы для VLAN 20 и VLAN 30
7. Также создаем сабинтерфейс для VLAN 2 и делаем его нативным **encapsulation dot1Q 2 native**

## Настройка Sw1 и Sw2
1. Заходим в превелегированый режим **enable**
2. Переходим в режим глобальной конфигурации **configure terminal**
3. Создаём VLAN 2  **vlan 2** 
4. Аналогичным образом создаём и VLANs 10, 20 и 30
5. ***Настраиваем trunk порты***
6. Переходим в интерфейс Gi0/0 **interface GigabitEthernet0/0**
7. Задаем интефейсу работу с VLAN  **switchport trunk encapsulation dot1q**
8. Назначим транковые VLANs **switchport trunk allowed vlan 2,10,20,30**
9. Говорим что VLAN 2 нативный **switchport trunk native vlan 2**
10. Переводим порт в режим trunk  **switchport mode trunk**
11. Выключаем передачу сообщений DTP  **switchport nonegotiate**
12. Аналогичным образом настраивае транковые порты
13. ***Настраиваем access порты***
14. Переходим в интерфейс Gi0/1 **interface GigabitEthernet0/1**
15. Переводим порт в режим access **switchport mode access**
16. Говорим что порт работает в 10 vlan **switchport access vlan 10**
17. Выключаем передачу сообщений DTP  **switchport nonegotiate**
18. Аналогичным образом настраивае порты для VLANs 20 и 30
