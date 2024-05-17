### How to Install Certbot in Apache2

- Install certbot

```
sudo apt install certbot python3-certbot-apache
```

- Make sure your configuration are all correct and have A records that target your public ip address

- Install certbot apache

```
sudo certbot --apache
```

- Once installing is done, Enable the SSL Module

```
sudo a2enmod ssl
```

- Setup your updated configuration that will make your http request redirect in https. Make sure you setup port 443 for https

```
<VirtualHost *:80>
    ServerAdmin webmaster@localhost
    ServerName iacat-icms.com
    ServerAlias www.iacat-icms.com
    DocumentRoot "/var/www/html/icms-main/public_html"

    ErrorLog ${APACHE_LOG_DIR}/error.log
    CustomLog ${APACHE_LOG_DIR}/access.log combined

    RewriteEngine On
    RewriteCond %{HTTPS} off
    RewriteRule ^ https://%{HTTP_HOST}%{REQUEST_URI} [L,R=301]
</VirtualHost>

<VirtualHost *:443>
    ServerAdmin webmaster@localhost
    ServerName iacat-icms.com
    ServerAlias www.iacat-icms.com
    DocumentRoot "/var/www/html/icms-main/public_html"

    ErrorLog ${APACHE_LOG_DIR}/error.log
    CustomLog ${APACHE_LOG_DIR}/access.log combined

    SSLEngine on
    SSLCertificateFile /etc/letsencrypt/live/iacat-icms.com/fullchain.pem
    SSLCertificateKeyFile /etc/letsencrypt/live/iacat-icms.com/privkey.pem
</VirtualHost>

```


### Additional syntax
- Check the Configuration File for Syntax Errors `sudo apachectl configtest`



