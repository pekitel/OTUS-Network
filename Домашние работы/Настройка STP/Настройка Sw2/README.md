## Настройка Sw2
1. Заходим в превилегированый режим **enable**
2. Переходим в режим конфигурации **configure terminal**
3. Задаём имя для коммутатора **hostname Sw2**
>![15](https://user-images.githubusercontent.com/112701413/190697571-a565d213-3df6-4660-a522-a00fbaa86884.jpg)
4. Создаём VLAN 2  **vlan 2** 
5. Аналогичным образом создаём и VLANs 10, 20 ,30 и 40
>![16](https://user-images.githubusercontent.com/112701413/190698232-ec388eed-9aee-4727-a291-cbbf064752c0.jpg)
6. Включаем протокол STP **spanning-tree mode rapid-pvst**
>![17](https://user-images.githubusercontent.com/112701413/190698801-43a9051b-7c6d-46ea-a06b-6aca88fcc130.jpg)
7. ***Настраиваем trunk порты***
8. Переходим в интерфейсы Gi0/1 и Gi0/2 **interface range gigabitEthernet 0/1-2**
9. Назначим транковые VLANs **switchport trunk allowed vlan 2,10,20,30**
10. Назначим VLAN 2 нативный **switchport trunk native vlan 2**
11. Переводим порт в режим trunk **switchport mode trunk**
12. Выключаем передачу сообщений DTP **switchport nonegotiate**
>![18](https://user-images.githubusercontent.com/112701413/190699478-4fa93a03-5e5c-45c1-ae73-53304ca6cefd.jpg)
13. Записываем конфигурация во flash память **do wr**
14. ***Настраиваем access порты***
15. Переходим в интерфейс Fa0/1 **interface fastEthernet 0/1**
16. Переводим порт в режим access **switchport mode access**
17. Настраиваем порт для работы в 30 vlan **switchport access vlan 30**
>![19](https://user-images.githubusercontent.com/112701413/190700590-1adc93e8-b4ce-4c5f-9ed4-0b2b337d760d.jpg)
18. Выключаем передачу сообщений DTP  **switchport nonegotiate**
19. Включаем *portfast* **spanning-tree portfast**
20. Отключаем получения BPDU пакетов **spanning-tree bpduguard enable**
21. Записываем конфигурация во flash память **do wr**
>![20](https://user-images.githubusercontent.com/112701413/190700847-d2a16eb1-df97-465b-8493-cabd0b0b2103.jpg)
22. Аналогичным образом настраиваем порт fa0/2 для Vlan 10
