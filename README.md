**Разворачиваем сетевую лабораторию**

**1. Описание задания**
В виртуальной среде виртуалбок при помощи вагрант файл разварачиваю несколько виртуальных хостов, часть из них будут являтьс маршутизаторами: inetRouter, centralRouter, office1Router, office2Router, часть из них будут являться серверами: centarlServer, office1Server, office2Server.

Планируемая архитектура.

Сеть inetRouter
10.0.2.15/24 - интеренет
192.168.255.1/30 - локальная сеть

Сеть centralRouter.
192.168.0.0/28 - directors
192.168.0.32/28 - office hardware
192.168.0.64/26 - wifi
192.168.255.0/30 локальная сеть

Сеть office1.
192.168.2.0/26 - dev
192.168.2.64/26 - test servers
192.168.2.128/26 - managers
192.168.2.192/26 - office hardware

Сеть office2.
192.168.1.0/25 - dev
192.168.1.128/26 - test servers
192.168.1.192/26 - office hardware

```
Office1 ---\
----> Central --IRouter --> internet
Office2----/
```
**Необходимо**: автоматизировать настройку хостов через вагрантфайл:

1. Соединить офисы в сеть согласно схеме и настроить роутинг.
2. Все сервера и роутеры должны ходить в инет черз inetRouter.
3. Все сервера должны видеть друг друга.
4. У всех серверов отключить дефолт на нат (eth0), который вагрант поднимает для связи.

 **2. Выполенение задания.**
 В ручном режиме подключаясь по ssh  сконфигурировал узыл.
 
1. inetRouter
- настроил ipforwarding
- настроил NAT
- настроил обратный маршрут для пересылки с ната в локлаку.

2. centralRouter
- отключил дефолтный маршрут на eth0
- включил дефолтный маршрут на eth1 192.168.255.1
- настроил ipforwarding

3. centarlServer
- отключил дефолтный маршрут на eth0
- включил дефолтный маршрут на eth1 192.168.0.1

4. office1Router
- отключил дефолтный маршрут на eth0
- включил дефолтный маршрут на eth1 192.168.255.9
- настроил ipforwarding

5. office2Router
- отключил дефолтный маршрут на eth0
- включил дефолтный маршрут на eth1 192.168.255.5
- настроил ipforwarding

6. office1Server
- отключил дефолтный маршрут на eth0
- включил дефолтный маршрут на eth1 192.168.2.1

7. office2Server
- отключил дефолтный маршрут на eth0
- включил дефолтный маршрут на eth1 192.168.1.1
