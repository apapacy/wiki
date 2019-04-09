<!-- TITLE: Nginx -->
<!-- SUBTITLE: A quick summary of Nginx -->


# Установка Nginx

1. Установка веб-сервера Nginx:

`apt update && apt install nginx`

2. Настройка файрвола:

```text
ufw allow 'Nginx HTTP'
ufw allow 'Nginx HTTPS'
ufw allow ssh
```

3. Проверка статуса UFW:

`ufw status`

4. Если всё верно, то включаем UFW:

`ufw enable`

5. Проверка статуса Nginx:

`systemctl status nginx`


# Команды Nginx

1. Перезагрузка конфигурации:

`systemctl reload nginx`

2. Проверка конфигурации:

`nginx -t`

3. Полная перезагрузка Nginx:

`systemctl restart nginx`


-----


Настройка конфигураций Nginx:

**/etc/nginx/sites-available/example.com**



-----


