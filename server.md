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
2. Установка актуальной версии NodeJS:
```text
curl -sL https://deb.nodesource.com/setup_11.x | sudo -E bash -
```
Актуальная версия: https://github.com/nodesource/distributions/blob/master/README.md#debinstall
[Актуальная версия тут](https://github.com/nodesource/distributions/blob/master/README.md#debinstall){:target='_blank'}
