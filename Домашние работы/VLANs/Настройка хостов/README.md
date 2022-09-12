## Настройка R1
1. Заходим в превилегированый режим **enable**
2. Переходим в режим конфигурации устройства **configure terminal**
3. Задаём имя для роутера **hostname R1**
>![1](https://user-images.githubusercontent.com/112701413/189698770-fa6f5f81-f215-4878-98aa-78ae22549d72.jpg)
4. Создаём сабинтерфейс для VLAN 10  **interface gigabitEthernet 0/0.10**
5. Задаем интефейсу работу с VLAN 10  **encapsulation dot1Q 10**
6. Задаем ip адрес и маску подсети  **ip address 192.168.10.1 255.255.255.0**
>![2](https://user-images.githubusercontent.com/112701413/189699752-132eb6bd-3e2d-4f52-ae22-88ab3d115c5e.jpg)
7. Записываем конфигурация во flash память **do wr**
8. Аналогичным образом (п3-6) создаём и настраиваем сабинтерфейсы для VLAN 20 и VLAN 30
9. Также создаем сабинтерфейс для VLAN 2 и делаем его нативным **encapsulation dot1Q 2 native**
>![3](https://user-images.githubusercontent.com/112701413/189700617-c325b4d6-5767-4287-adef-a7825076d4d6.jpg)
## Настройка Sw1 и Sw2
1. Заходим в превилегированый режим **enable**
2. Переходим в режим конфигурации **configure terminal**
3. Задаём имя для коммутатора **hostname Sw1**
>![4](https://user-images.githubusercontent.com/112701413/189706233-77643bf9-167e-4995-8150-80d963f15fbb.jpg)
4. Создаём VLAN 2  **vlan 2** 
5. Аналогичным образом создаём и VLANs 10, 20 и 30
>![5](https://user-images.githubusercontent.com/112701413/189706711-f19118f3-9871-4e44-b0dd-eab291cb1998.jpg)
6. ***Настраиваем trunk порты***
7. Переходим в интерфейс Gi0/0 **interface GigabitEthernet0/0**
8. Задаем интефейсу работу с VLAN  **switchport trunk encapsulation dot1q**
9. Назначим транковые VLANs **switchport trunk allowed vlan 2,10,20,30**
>![6](https://user-images.githubusercontent.com/112701413/189707614-ccd98760-c2a4-458b-af02-d3d49f234454.jpg)
10. Назначим VLAN 2 нативный **switchport trunk native vlan 2**
11. Переводим порт в режим trunk  **switchport mode trunk**
12. Выключаем передачу сообщений DTP  **switchport nonegotiate**
13. Записываем конфигурация во flash память **do wr**
>![7](https://user-images.githubusercontent.com/112701413/189707984-1a9fa236-4b58-44dd-9288-5cca15ebe15c.jpg)
14. Аналогичным образом (п7-12) настраиваем транковый порты *Gi1/0* на *Sw1* и *Gi1/0* на *Sw2*
15. ***Настраиваем access порты***
16. Переходим в интерфейс Gi0/1 **interface GigabitEthernet0/1**
17. Переводим порт в режим access **switchport mode access**
18. Настраиваем порт для работы в 10 vlan **switchport access vlan 10**
>![8](https://user-images.githubusercontent.com/112701413/189708599-c21a7be6-8280-4962-a19a-40f96932dda7.jpg)
19. Выключаем передачу сообщений DTP  **switchport nonegotiate**
20. Записываем конфигурация во flash память **do wr**
>![9](https://user-images.githubusercontent.com/112701413/189708968-6ba15280-be36-4577-813c-9694bfec925a.jpg)
21. Аналогичным образом (п15-18) настраиваем порты для VLANs 20 и 30
## Настраиваем PC
1. Задаем ip адрес для PC1  **ip 192.168.10.10 255.255.255.0 192.168.10.1**
2. Сохраняем настройки **save**
>![10](https://user-images.githubusercontent.com/112701413/189709701-1444c263-9439-4542-ba81-5a042853bdec.jpg)
3. Аналогичным образом настраиваем остальные PC для каждого VLAN
