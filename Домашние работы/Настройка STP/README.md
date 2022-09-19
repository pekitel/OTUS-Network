# STP


## Схема сети
![Схема сети RSTP](https://user-images.githubusercontent.com/112701413/190674967-a550f022-a0b1-4739-a27e-bf13dc81209c.jpg)

## ip address
VLAN | ip address | host |
:----: | :----------: | :----: |
10 | 192.168.10.10 | PC1 |
10 | 192.168.10.11 | PC4 |
10 | 192.168.10.12 | PC5 |
20 | 192.168.20.10 | PC6 |
20 | 192.168.20.10 | PC8 |
30 | 192.168.30.10 | PC2 |
30 | 192.168.30.11 | PC3 |
40 | 192.168.40.10 | PC7 |

## Настройка хостов
  1. [Настройка роутера](https://github.com/pekitel/OTUS-Network/tree/main/%D0%94%D0%BE%D0%BC%D0%B0%D1%88%D0%BD%D0%B8%D0%B5%20%D1%80%D0%B0%D0%B1%D0%BE%D1%82%D1%8B/%D0%9D%D0%B0%D1%81%D1%82%D1%80%D0%BE%D0%B9%D0%BA%D0%B0%20STP/%D0%9D%D0%B0%D1%81%D1%82%D1%80%D0%BE%D0%B9%D0%BA%D0%B0%20%D1%80%D0%BE%D1%83%D1%82%D0%B5%D1%80%D0%B0)
  2. [Настройка Sw1](https://github.com/pekitel/OTUS-Network/tree/main/%D0%94%D0%BE%D0%BC%D0%B0%D1%88%D0%BD%D0%B8%D0%B5%20%D1%80%D0%B0%D0%B1%D0%BE%D1%82%D1%8B/%D0%9D%D0%B0%D1%81%D1%82%D1%80%D0%BE%D0%B9%D0%BA%D0%B0%20STP/%D0%9D%D0%B0%D1%81%D1%82%D1%80%D0%BE%D0%B9%D0%BA%D0%B0%20Sw1)
  3. [Настройка Sw2](https://github.com/pekitel/OTUS-Network/blob/main/%D0%94%D0%BE%D0%BC%D0%B0%D1%88%D0%BD%D0%B8%D0%B5%20%D1%80%D0%B0%D0%B1%D0%BE%D1%82%D1%8B/%D0%9D%D0%B0%D1%81%D1%82%D1%80%D0%BE%D0%B9%D0%BA%D0%B0%20STP/%D0%9D%D0%B0%D1%81%D1%82%D1%80%D0%BE%D0%B9%D0%BA%D0%B0%20Sw2)
  4. [Настройка Sw3](https://github.com/pekitel/OTUS-Network/tree/main/%D0%94%D0%BE%D0%BC%D0%B0%D1%88%D0%BD%D0%B8%D0%B5%20%D1%80%D0%B0%D0%B1%D0%BE%D1%82%D1%8B/%D0%9D%D0%B0%D1%81%D1%82%D1%80%D0%BE%D0%B9%D0%BA%D0%B0%20STP/%D0%9D%D0%B0%D1%81%D1%82%D1%80%D0%BE%D0%B9%D0%BA%D0%B0%20Sw3)
  5. [Настройка Sw4](https://github.com/pekitel/OTUS-Network/tree/main/%D0%94%D0%BE%D0%BC%D0%B0%D1%88%D0%BD%D0%B8%D0%B5%20%D1%80%D0%B0%D0%B1%D0%BE%D1%82%D1%8B/%D0%9D%D0%B0%D1%81%D1%82%D1%80%D0%BE%D0%B9%D0%BA%D0%B0%20STP/%D0%9D%D0%B0%D1%81%D1%82%D1%80%D0%BE%D0%B9%D0%BA%D0%B0%20Sw4)
  6. [Настройка Sw5](https://github.com/pekitel/OTUS-Network/tree/main/%D0%94%D0%BE%D0%BC%D0%B0%D1%88%D0%BD%D0%B8%D0%B5%20%D1%80%D0%B0%D0%B1%D0%BE%D1%82%D1%8B/%D0%9D%D0%B0%D1%81%D1%82%D1%80%D0%BE%D0%B9%D0%BA%D0%B0%20STP/%D0%9D%D0%B0%D1%81%D1%82%D1%80%D0%BE%D0%B9%D0%BA%D0%B0%20Sw5)

## Проверка
  Так как на Sw1 для Vlan 10 приоритетный маршрут через интерфейс Gi0/1, то проверим что произайдет если пропадет *link* на этом парту

>![43](https://user-images.githubusercontent.com/112701413/190961183-143efe2d-1a8b-4de7-aaa8-f089c657586b.jpg)
 
 Запустим *icmp* запросы от PC1 до PC5 и выключим порт Gi0/1 на Sw1

>  ![44](https://user-images.githubusercontent.com/112701413/190961216-c1da368a-03ec-40e3-b560-51c8a72822e5.jpg)

Видим что STP перестроил ципочку дерева и связь востановилась через порт Gi0/2
Порт Gi0/1 поменял режим с *alternative* на *root* , а порт Gi0/2 поменял режим c *root* на *Designated*
>![45](https://user-images.githubusercontent.com/112701413/190962311-07929c0b-f057-427a-af4a-9a4d1f38b06c.jpg)

