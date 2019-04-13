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
