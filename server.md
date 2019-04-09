<!-- TITLE: Базовая настройка сервера -->
<!-- SUBTITLE: A quick summary of Server -->

# Обновление до Ubuntu 18.04
1. Обновление пакетов:
```text
apt-get update && apt-get upgrade && apt-get dist-upgrade
```
2. Удаление мусора:
```text
apt-get autoremove
```
3. Перезагрузка (обязательно):
```text
reboot
```
4. Обновление до Ubuntu 18.04
```text
do-release-upgrade -d
```



-----



# Установка NODE JS
1. Установка CURL (если не установлен):
```text
apt-get install curl
```
2. Выбор актуальной версии NodeJS:
```text
curl -sL https://deb.nodesource.com/setup_11.x | sudo -E bash -
```
Актуальная версия: [https://github.com/nodesource/distributions/blob/master/README.md#debinstall](https://github.com/nodesource/distributions/blob/master/README.md#debinstall){target="_blank"}

3. Установка:

```text
apt-get install -y nodejs
```

4. Дополнения:

```text
apt-get install -y build-essential
```



-----



# Установка GIT


```text
apt-get install git
```



-----


# Установка PM2


```text
 npm install pm2@latest -g
```


Добавление в автозагрузку:

```text
pm2 startup systemd
```



-----



# Установка MongoDB

Рассмотрена установка MongoDB 4.0

Официальная документация тут: 
[https://docs.mongodb.com/manual/tutorial/install-mongodb-on-ubuntu/#import-the-public-key-used-by-the-package-management-system](https://docs.mongodb.com/manual/tutorial/install-mongodb-on-ubuntu/#import-the-public-key-used-by-the-package-management-system){target='_blank'}


```text
sudo apt-key adv --keyserver hkp://keyserver.ubuntu.com:80 --recv 9DA31620334BD75D9DCB49F368818C72E52529D4
```


```text
echo "deb [ arch=amd64 ] https://repo.mongodb.org/apt/ubuntu bionic/mongodb-org/4.0 multiverse" | sudo tee /etc/apt/sources.list.d/mongodb-org-4.0.list
```


```text
sudo apt-get update
```


```text
sudo apt-get install -y mongodb-org
```

