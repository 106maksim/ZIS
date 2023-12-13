# Отчет выполнил студент группы ББМО-01-23 Бакин Д.И.

### Загрузка

```
git clone https://github.com/Ivanhahanov/InformtionsSecurityMethodsAndTools.git
```
![Загрузка](https://github.com/xoz0r/Protected-Inform-Tech/assets/145142526/ee4fe80a-8b48-4f62-8eb5-5fe4bb7dd9c0)

### Развертывание

1. Запустить Honeypot

```
cd Deception
docker-compose up
```
![Развертывание 1](https://github.com/xoz0r/Protected-Inform-Tech/assets/145142526/c88063f3-176f-48dd-bb11-8a2d3a621c16)

Запускаем Honeypot для отслеживания активности злоумышленника

2. Сделать файл исполняемым и запустить

```
chmod +x hackersActivity
./hackersActivity
```
![Развертывание 2](https://github.com/xoz0r/Protected-Inform-Tech/assets/145142526/1664979a-0553-44ce-a253-9eafd63321da)

Запускаем файл, который будет имитировать активность злоумышленника

3. Открыть логи honeypot

```
docker-compose logs -f
```

![Развертывание 3](https://github.com/xoz0r/Protected-Inform-Tech/assets/145142526/f2399abb-9134-4208-8834-45ab31cf60e8)

Наблюдаем за действиями злоумышленника, которые выводит Honeypot

# Посмотрим активность злоумышленника через логи 
## SSH
подключение по кредам root/root
```
honeypot_1 | services > ssh > category=ssh, date=2023-10-31
18:37:54.732135644 +0000 UTC m=+93.988681664, destinationip=172.20.0.2, destination-port=8022, sensor=services, sourceip=172.20.0.1, source-port=59448, ssh.password=root,
ssh.sessionid=cl0kj0gdkej0009e49ug, ssh.username=root,
token=cl0ki90dkej0009e49sg, type=password-authentication
```
## Выполнение команд
“pwd” - выводит полный путь от корневого каталога к текущему рабочему каталогу

“ip a” - информация о подключениях хост

“ls -la” - отображает все файлы в директории включая скрытые

“cat /etc/shadow“ - отображает содержимое файла “shadow”

![image](https://github.com/xoz0r/Protected-Inform-Tech/assets/145142526/ec986fa9-d587-407e-915e-14e3e5e1aab5)

## Telnet
подключение по кредам root/root
```
honeypot_1 | services > telnet > category=telnet, date=2023-10-31
18:38:29.740860099 +0000 UTC m=+128.997406109, destinationip=172.20.0.2, destination-port=8023, sensor=services, sourceip=172.20.0.1, source-port=54782, telnet.password=root,
telnet.sessionid=cl0kj98dkej0009e49v0, telnet.username=root,
token=cl0ki90dkej0009e49sg, type=password-authentication
```
## Выполнение команд
display arp interface GigabitEthernet 0/0/1 – ARP записи, относящиеся к указанному интерфейсу

display ip vpn-instance - отображает конфигурацию сервера VPN

display arp - все ARP записи

display session limit vpn-instance vpna – количество возможных подключений к VPN

display snmp-server arp-sync table – ARP записи, синхронизированные через SNMP

![image](https://github.com/xoz0r/Protected-Inform-Tech/assets/145142526/db425335-4755-4de0-9eb0-96e5aa79e1d5)

## Http
Переход по оставленным в открытом доступе страницам

robots.txt

login.php - страница логина

admin.php - страница админ панели

sitemap.xml - карта сайта

![image](https://github.com/xoz0r/Protected-Inform-Tech/assets/145142526/25c3f49a-8225-45e4-b7de-7ec927b20453)

## Redis
Команды
INFO – информация о базе данны

GET admin - возвращение значения по ключу admin - вероятно вся информация о пользователе

CONFIG GET * - используется для чтения параметров конфигурации Redis

KEYS * - возвращение всех ключей из базы

CLIENT LIST - возвращение информацию и статистику о клиентских подключениях

![image](https://github.com/xoz0r/Protected-Inform-Tech/assets/145142526/cb8c7de1-b054-4634-9fd5-47bdaefc84ad)

FTP
Подключение по кредам anonymous/anonymous

![image](https://github.com/xoz0r/Protected-Inform-Tech/assets/145142526/d2a31f93-4295-42e7-8807-4a8b9d1f347a)

Выполняемые команды
FEAT – показывает дополнительные команды, поддерживаемые сервером

APPE /exploit.sh – загружает файл exploit.sh

PWD – получает имя текущего каталога

STOR /etc/passwd – заменяет файл passwd на хосте

HELP - выводит команды FTP

LIST -l – выводит список файлов

![image](https://github.com/xoz0r/Protected-Inform-Tech/assets/145142526/d081427f-f68f-473a-aefd-764079ac03a5)

