# Настройка и проверка DHCP

Скриншоты учебного стенда: базовая настройка маршрутизатора, DHCP-сервера и проверка выдачи адреса клиенту.

## 1. Настройка маршрутизатора

![Настройка R1 — часть 1](https://github.com/user-attachments/assets/41c674b0-3b61-4cba-b511-b3d13bbfb2cc)

![Настройка R1 — часть 2](https://github.com/user-attachments/assets/733a612b-a8f6-4e54-9ec4-e4694ff0093c)

## 2. Настройка DHCP-сервера

![Параметры DHCP — шаг 1](https://github.com/user-attachments/assets/da360357-96a8-436a-a8b0-9acc44623780)

![Параметры DHCP — шаг 2](https://github.com/user-attachments/assets/9f0dc040-c73e-480d-a2b5-3a5dc8710595)

![Параметры DHCP — шаг 3](https://github.com/user-attachments/assets/3558bb2e-7193-41ef-830b-1fb718e9a167)

![Параметры DHCP — шаг 4](https://github.com/user-attachments/assets/77db4783-b6a2-4b74-ab18-0c6b3cbb44c5)

![Параметры DHCP — шаг 5](https://github.com/user-attachments/assets/c627e4d5-b227-47bf-bf4f-72ab3b8ec159)

![Параметры DHCP — шаг 6](https://github.com/user-attachments/assets/889d004a-81a8-4261-b7c0-63a94a36c3ff)

![Параметры DHCP — шаг 7](https://github.com/user-attachments/assets/d3e4e8aa-f2e8-48c9-97a5-0cedbff76434)

![Параметры DHCP — шаг 8](https://github.com/user-attachments/assets/f388bbb4-d5a4-4216-8b1a-493d3df14fca)

## 3. Проверка на клиенте

Клиент получил IP-адрес от DHCP-сервера. Дополнительно проверена доступность внешней сети через NAT.

![Получение IP-адреса и проверка доступности сети](https://github.com/user-attachments/assets/75f2c9c4-7dfa-45ef-8bf9-100f472148f9)

## Контрольные точки

- Адрес клиента относится к правильной подсети VLAN.
- Шлюз по умолчанию совпадает с адресом сабинтерфейса R1.
- Клиент получает адрес автоматически, без ручной настройки.
- Маршрутизация между VLAN и NAT-трансляции работают.
