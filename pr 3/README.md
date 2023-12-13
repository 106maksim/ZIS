# Отчет выполнил студент группы ББМО-01-23 Куров М.В.

### Развертывание

1. Запустить Honeypot

```
cd Deception
docker-compose up
```

![развёртывание 1](https://github.com/106maksim/ZIS/assets/71127999/a78c2ab0-8d77-483a-867d-3bb583d43457)

Запускаем Honeypot для отслеживания активности злоумышленника

2. Сделать файл исполняемым и запустить

```
chmod +x hackersActivity
./hackersActivity
```

![развёртывание 2](https://github.com/106maksim/ZIS/assets/71127999/5effb143-0d9c-4ea8-90a4-a266d81dbdf5)

Запускаем файл, который будет имитировать активность злоумышленника

3. Открыть логи honeypot

```
docker-compose logs -f
```

![развёртывание 3](https://github.com/106maksim/ZIS/assets/71127999/3575277f-9338-4c3e-89aa-eacadb4bf844)

Наблюдаем за действиями злоумышленника, которые выводит Honeypot

# Посмотрим активность злоумышленника через логи 
## SSH
подключение по кредам root/root

![image](https://github.com/106maksim/ZIS/assets/71127999/06094b34-d97e-4fa9-884c-12974ba2992c)

## Выполнение команд
“pwd” - выводит полный путь от корневого каталога к текущему рабочему каталогу

“ip a” - информация о подключениях хост

“crontab -l” - показать содержимое файла “crontab”

“ls -la” - отображает все файлы в директории включая скрытые

“cat /etc/shadow“ - отображает содержимое файла “shadow”

![image](https://github.com/106maksim/ZIS/assets/71127999/71a67539-9e2e-4a72-b11e-4634594af694)

## Telnet
подключение по кредам root/root

![image](https://github.com/106maksim/ZIS/assets/71127999/0a6ba81c-d455-4981-bb71-59e4ac9b159d)

## Выполнение команд
system-view - переход в системный режим из пользовательского режима.

display snmp-server arp-sync table – ARP записи, синхронизированные через SNMP

display arp interface GigabitEthernet 0/0/1 – ARP записи, относящиеся к указанному интерфейсу

display ipsec-tunnel limit vpn-instance vpna - количество возможных подключений к VPN

display ip vpn-instance - отображает конфигурацию сервера VPN

![image](https://github.com/106maksim/ZIS/assets/71127999/f697290a-d88e-4e8b-b94e-b33a56dacedc)

## Http
Переход по оставленным в открытом доступе страницам

robots.txt

login.php - страница логина

admin.php - страница админ панели

sitemap.xml - карта сайта

![image](https://github.com/106maksim/ZIS/assets/71127999/b639d8fa-48f8-47cd-a37b-1d3ac4647dc1)

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

