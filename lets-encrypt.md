<!-- TITLE: Let's Encrypt -->
<!-- SUBTITLE: A quick summary of Lets Encrypt -->

# Шаг 1 - Установка Certbot

Сначала добавим репозиторий:

`add-apt-repository ppa:certbot/certbot`

Установим пакет Certbot для Nginx с помощью apt:

`apt install python-certbot-nginx`


**Важно!**
Необходимо проверить настройки Nginx и разрешения в UFW



-----


# Получение SSL сертификата

`certbot --nginx -d example.com -d www.example.com`




-----


#  Проверка автоматического обновления сертификата

`certbot renew --dry-run`




-----

