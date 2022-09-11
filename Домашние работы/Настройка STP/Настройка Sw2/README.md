## Настройка Sw2
1. Заходим в превилегированый режим **enable**
2. Переходим в режим конфигурации **configure terminal**
3. Задаём имя для коммутатора **hostname Sw2**
4. Создаём VLAN 2  **vlan 2** 
5. Аналогичным образом создаём и VLANs 10, 20 ,30 и 40
6. Включаем протокол STP **spanning-tree mode rapid-pvst**
7. Настраивае приоритет для VLANs 30,40 **spanning-tree vlan 30,40 priority 4096**
> 
