# Конфигурация маршрутизатора R1

Cisco 7200, Cisco IOS 15.3. Конфигурация учебного стенда: сабинтерфейсы для VLAN 10/20/30, DHCP relay, NAT overload и удалённый доступ по SSH.

> Команды приведены для лаборатории. Перед применением сверяйте интерфейсы, IP-адреса и имена узлов с топологией.

## 1. Базовые параметры и SSH

```cisco
enable
configure terminal
enable secret cisco
service password-encryption
hostname router1
username admin_R privilege 15 secret cisco
ip domain-name test.local
crypto key generate rsa general-keys modulus 2048

line console 0
exit
line vty 0 15
transport input ssh
exit
```

## 2. Основной интерфейс и сабинтерфейсы VLAN

```cisco
interface GigabitEthernet1/0
no shutdown
exit

interface GigabitEthernet1/0.10
encapsulation dot1Q 10
ip address 192.168.10.1 255.255.255.0
ip nat inside
exit

interface GigabitEthernet1/0.20
encapsulation dot1Q 20
ip address 192.168.20.1 255.255.255.0
ip helper-address 192.168.102.2
ip nat inside
exit

interface GigabitEthernet1/0.30
encapsulation dot1Q 30
ip address 192.168.30.1 255.255.255.0
ip helper-address 192.168.102.2
ip nat inside
exit
```

## 3. Внешний интерфейс

Интерфейс `FastEthernet0/0` получает адрес по DHCP от NAT-сети GNS3 и выполняет роль `outside`.

```cisco
interface FastEthernet0/0
no shutdown
ip address dhcp
ip nat outside
exit
```

## 4. NAT overload

```cisco
access-list 1 permit 192.168.10.0 0.0.0.255
access-list 1 permit 192.168.20.0 0.0.0.255
access-list 1 permit 192.168.30.0 0.0.0.255
ip nat inside source list 1 interface FastEthernet0/0 overload
ip routing
end
```

## 5. Проверка

```cisco
show ip interface brief
show ip nat translations
show ip nat statistics
show ip ssh
show running-config
```

Ожидаемый результат: сабинтерфейсы активны, DHCP-запросы перенаправляются серверу, в таблице NAT появляются трансляции, а подключение к маршрутизатору по SSH выполняется успешно.
