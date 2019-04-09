<!-- TITLE: Базовая настройка сервера -->
<!-- SUBTITLE: A quick summary of Server -->

# Обновление до Ubuntu 18.04
1. Обновление пакетов:

`apt-get update && apt-get upgrade && apt-get dist-upgrade`

2. Удаление мусора:

`apt-get autoremove`

3. Перезагрузка (обязательно):

`reboot`

4. Обновление до Ubuntu 18.04

`do-release-upgrade -d`



-----



# Установка NODE JS
1. Установка CURL (если не установлен):

`apt-get install curl`

2. Выбор актуальной версии NodeJS:

`curl -sL https://deb.nodesource.com/setup_11.x | sudo -E bash -`

Актуальная версия: [https://github.com/nodesource/distributions/blob/master/README.md#debinstall](https://github.com/nodesource/distributions/blob/master/README.md#debinstall){target="_blank"}

3. Установка:

`apt-get install -y nodejs`

4. Дополнения:

`apt-get install -y build-essential`



-----



# Установка GIT

`apt-get install git`



-----


# Установка PM2


`npm install pm2@latest -g`


Добавление в автозагрузку:

`pm2 startup systemd`



-----



# Установка MongoDB

Рассмотрена установка MongoDB v4.0

Официальная документация тут: 
[https://docs.mongodb.com/manual/tutorial/install-mongodb-on-ubuntu/#import-the-public-key-used-by-the-package-management-system](https://docs.mongodb.com/manual/tutorial/install-mongodb-on-ubuntu/#import-the-public-key-used-by-the-package-management-system){target='_blank'}

1. Импортируем открытый ключ, используемый системой управления пакетами: 

`apt-key adv --keyserver hkp://keyserver.ubuntu.com:80 --recv 9DA31620334BD75D9DCB49F368818C72E52529D4`

2. Создаем файл списка для установки:

`echo "deb [ arch=amd64 ] https://repo.mongodb.org/apt/ubuntu bionic/mongodb-org/4.0 multiverse" | tee /etc/apt/sources.list.d/mongodb-org-4.0.list`

3. Перезагрузка пакетов для установки:

`apt-get update`

4. Установка пакетов MongoDB:

`apt-get install -y mongodb-org`

Готово!


# Настройка MongoDB
1. Запуск сервиса mongo:

`service mongod start`

2. Настройка mongo.config


```yaml
net:
  port: 27017
  bindIp: 127.0.0.1, ***serverIP***


security:
  authorization: 'enabled'
```

