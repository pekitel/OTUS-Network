## Настройка Sw5
1. Заходим в превилегированый режим **enable**
2. Переходим в режим конфигурации **configure terminal**
3. Задаём имя для коммутатора **hostname Sw5**
>![31](https://user-images.githubusercontent.com/112701413/190720161-766d1c84-84e9-46c4-87ed-dab43700fa23.jpg)
4. Создаём VLAN 10 **vlan 10**
5. Включаем протокол RSTP **spanning-tree mode rapid-pvst**
>![32](https://user-images.githubusercontent.com/112701413/190722705-bf4e944f-328d-4966-9030-c041bd35b41a.jpg)
6. ***Настраиваем access порты***
7. Переходим в интерфейсы Fa0/1, Fa0/2 и Fa0/3 **interface range fastEthernet 0/1-3**
8. Переводим порты в режим access **switchport mode access**
9. Настраиваем порты для работы в 10 vlan **switchport access vlan 10**
10 Записываем конфигурация во flash память **do wr**
>![33](https://user-images.githubusercontent.com/112701413/190725588-c954f9a8-6ab4-4f03-9633-821c5ba522e3.jpg)
11. Посмотрим режим портов spanning-tree для VLANs 10 **sh spanning-tree vlan 10**
>![34](https://user-images.githubusercontent.com/112701413/190727393-581e0e91-8e74-47da-a4f1-467c17c7816c.jpg)
12. Видим что порт Fa0/1 перешёл в режим *root* , а порт Fa0/2 перешёл в режим *alternative* (для предотвращение петли)
