## Настройка R1
1. Заходим в превилегированый режим **enable**
2. Переходим в режим конфигурации устройства **configure terminal**
3. Задаём имя для роутера **hostname R1**
4. Создаём сабинтерфейс для VLAN 10  **interface gigabitEthernet 0/0.10**
5. Задаем интефейсу работу с VLAN 10  **encapsulation dot1Q 10**
6. Задаем ip адрес и маску подсети  **ip address 192.168.10.1 255.255.255.0**
7. Записываем конфигурация во flash память **do wr**
8. Аналогичным образом (п3-6) создаём и настраиваем сабинтерфейсы для VLAN 20, VLAN 30 и VLAN 40
9. Также создаем сабинтерфейс для VLAN 2 и делаем его нативным **encapsulation dot1Q 2 native**
[config](https://github.com/pekitel/OTUS-Network/blob/main/%D0%94%D0%BE%D0%BC%D0%B0%D1%88%D0%BD%D0%B8%D0%B5%20%D1%80%D0%B0%D0%B1%D0%BE%D1%82%D1%8B/%D0%9D%D0%B0%D1%81%D1%82%D1%80%D0%BE%D0%B9%D0%BA%D0%B0%20STP/%D0%9D%D0%B0%D1%81%D1%82%D1%80%D0%BE%D0%B9%D0%BA%D0%B0%20%D1%80%D0%BE%D1%83%D1%82%D0%B5%D1%80%D0%B0/Config_R1)
