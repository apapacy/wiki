<!-- TITLE: Let's Encrypt -->
<!-- SUBTITLE: A quick summary of Lets Encrypt -->

# Установка Certbot

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


# Удаление домена

`certbot delete --cert-name example.com`


-----


#  Проверка автоматического обновления сертификата

`certbot renew --dry-run`




-----


# Пример настройки SSL


```json
server {
	server_name telegram.ml;
	location / {
		access_log off;
		proxy_pass http://localhost:5004/;
		proxy_http_version 1.1;
		proxy_set_header Upgrade $http_upgrade;
		proxy_set_header Connection 'upgrade';
		proxy_set_header Host $host;
		proxy_cache_bypass $http_upgrade;
	}
	location ~* ^.+\.(jpg|jpeg|gif|png|ttf|js|css)$ {           
		root /home/admin/telegram/public/;           
		expires 30d;
	}

    listen 443 ssl; # managed by Certbot
    ssl_certificate /etc/letsencrypt/live/telegram.ml/fullchain.pem; # managed by Certbot
    ssl_certificate_key /etc/letsencrypt/live/telegram.ml/privkey.pem; # managed by Certbot
    include /etc/letsencrypt/options-ssl-nginx.conf; # managed by Certbot
    ssl_dhparam /etc/letsencrypt/ssl-dhparams.pem; # managed by Certbot

}
server {
    if ($host = telegram.ml) {
        return 301 https://$host$request_uri;
    } # managed by Certbot


	server_name telegram.ml;

    listen 80;
    return 404; # managed by Certbot


}
```

-----

# Wild Certificate

###  Ручной режим

Получение Wild сертификата для вСервисе.рф

`certbot certonly --manual -d *.xn--b1aaibo0cfe.xn--p1ai -d xn--b1aaibo0cfe.xn--p1ai --agree-tos --no-bootstrap --manual-public-ip-logging-ok --preferred-challenges dns-01 --server https://acme-v02.api.letsencrypt.org/directory`

Получение Wild сертификата для in-services.ru

`certbot certonly --manual -d *.in-services.ru -d in-services.ru --agree-tos --no-bootstrap --manual-public-ip-logging-ok --preferred-challenges dns-01 --server https://acme-v02.api.letsencrypt.org/directory`



### Автоматический режим

Для всервисе.рф:

`sudo certbot --server https://acme-v02.api.letsencrypt.org/directory -d *.xn--b1aaibo0cfe.xn--p1ai --manual --preferred-challenges dns-01 certonly`

Для in-services.ru:

`sudo certbot --server https://acme-v02.api.letsencrypt.org/directory -d *.in-services.ru --manual --preferred-challenges dns-01 certonly`


Перезапуск Nginx:

`sudo /etc/init.d/nginx reload`