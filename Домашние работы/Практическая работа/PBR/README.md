# Задание

1. [Настроите политику маршрутизации для сетей офиса](https://github.com/pekitel/OTUS-Network/blob/main/%D0%94%D0%BE%D0%BC%D0%B0%D1%88%D0%BD%D0%B8%D0%B5%20%D1%80%D0%B0%D0%B1%D0%BE%D1%82%D1%8B/%D0%9F%D1%80%D0%B0%D0%BA%D1%82%D0%B8%D1%87%D0%B5%D1%81%D0%BA%D0%B0%D1%8F%20%D1%80%D0%B0%D0%B1%D0%BE%D1%82%D0%B0/PBR/README.md#%D0%BD%D0%B0%D1%81%D1%82%D1%80%D0%BE%D0%B9%D0%BA%D0%B0-%D0%BF%D0%BE%D0%BB%D0%B8%D1%82%D0%B8%D0%BA%D0%B8-%D0%BC%D0%B0%D1%80%D1%88%D1%80%D1%83%D1%82%D0%B8%D0%B7%D0%B0%D1%86%D0%B8%D0%B8-%D0%B4%D0%BB%D1%8F-%D1%81%D0%B5%D1%82%D0%B5%D0%B9-%D0%BE%D1%84%D0%B8%D1%81%D0%B0) 
2. [Распределите трафик между двумя линками с провайдером]()
3. Настроите отслеживание линка через технологию IP SLA.(только для IPv4)
4. Настройте для офиса Лабытнанги маршрут по-умолчанию.

## Схема сети

![PBR](https://user-images.githubusercontent.com/112701413/201127261-b5fd230b-9eeb-41e2-98ed-2fc23094a6d5.jpg)

| Hosts     | Port    | IPv4             | IPv6                   | Примечание      | Регион     |
|:---------:|:-------:|:----------------:|:-------------------:|:---------------:|:----------:|
| R27       | e0/0    | 110.10.1.2/30    | 2002:ABCD:0DB8:7::2    | R25(Triada)     | Лабытнанги |
| R28       | e0/0    | 77.37.10.6/30    | 2002:ABCD:0DB8:5::2    | R26(Triada)     | Чокурдах   |
|           | e0/1    | 77.37.10.2/30    | 2002:ABCD:0DB8:6::2    | R25(Triada)     |            |
|           | e0/2.10 | 40.200.10.1/24   | 2002:ABCD:0DB8: 100::1  | SW29(Chukordah) |            |
|           | e0/2.20 | 40.200.20.1/24   | 2002:ABCD:0DB8:200::1  | SW29(Chukordah) |            |
| VPC30     |         | 40.200.10.10     | 2002:ABCD:0DB8: 100::10 |                 |            |
| VPC31     |         | 40.200.20.10     | 2002:ABCD:0DB8:200::10 |                 |            |


#### Настройка политики маршрутизации для сетей офиса

**R28**
>![R28ipv6](https://user-images.githubusercontent.com/112701413/201130014-713112ca-e64e-4830-8c3b-03d1ace19fbf.jpg)
>![R28ipv4](https://user-images.githubusercontent.com/112701413/201131337-5f3848eb-9e67-4162-9a88-ff4fd51ad6a8.jpg)

**R25**
>![R25ipv6](https://user-images.githubusercontent.com/112701413/201132867-9499c3cb-04f2-4221-8a4f-ef790853703f.jpg)
>![R25ipv4](https://user-images.githubusercontent.com/112701413/201132874-90cde7e0-2b0e-4044-bca4-803e54334350.jpg)

**R26**
>![R25ipv6](https://user-images.githubusercontent.com/112701413/201133777-e4b3a9b8-008d-4ac2-83ed-b33c7b4e201d.jpg)
>![R25ipv4](https://user-images.githubusercontent.com/112701413/201133812-8b874438-a3b4-4e53-b8f5-2db5f82a3b2c.jpg)


#### Распределение трафика между двумя линками с провайдером
