# DHCP ipv6


#### Настройка [R1]
#### Настройка [R2]

## Схема сети

![ipv6](https://user-images.githubusercontent.com/112701413/193928748-a9eab94c-1479-4985-905b-4e1732a61fce.jpg)


  ## ipv6 address 
host | int | ip address |
:----:  | :----------: | :----: | 
R1 | e0/0 |2001:db8:acad:2::1/64 |
| | e0/1 | 2001:db8:acad:1::1/64 |
R2 | e0/0 | 2001:db8:acad:2::2/64 |
| | e0/1 | 2001:db8:acad:3::1/64 |
PC1 | eth0 | dhcp |
PC2 | eth0 | dhcp |
