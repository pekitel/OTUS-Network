# DHCP
  1. Настройка DHCP ipv4
  2. Настройка DHCP ipv6
  
  ## Схема сети
  
![dhcp](https://user-images.githubusercontent.com/112701413/192091532-16f77aea-a9df-43d8-b8a6-df5aedf01443.jpg)

  ## ipv4 address 
VLAN | ip address dhcp | excluded-address | host |
:----: | :----------: | :----: | :---: 
10 | 192.168.10.0/24 | 192.168.10.1-10| PC1 и PC3 
10 |                 | 192.168.10.254 |                     
