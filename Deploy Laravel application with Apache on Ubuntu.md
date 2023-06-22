# Deploy Laravel application with Apache on Ubuntu

1. update ubuntu first
    'sudo apt-get update
    sudo apt-get install apache2'

2. this is optional, only run if the php requirements are <= 8.2.6
<code>
    sudo add-apt-repository -y ppa:ondrej/php 
    sudo apt-get update
</code>
3. install all php package
<code>
    sudo apt install php php-cli php-mbstring php-xml php-zip php-mysql composer
</code>

5. search and change ;cgi.fix_pathinfo=1 into cgi.fix_pathinfo=0
<code>
    sudo nano /etc/php/8.2/apache2/php.ini
    sudo nano /etc/php/8.2/cli/php.ini
</code>

6. setup customize configuration
<code>
    sudo nano /etc/apache2/sites-available/laravel.conf

   <VirtualHost *:80>
        ServerAdmin 13.210.149.176
        ServerName 13.210.149.176
        ServerAlias 13.210.149.176
        DocumentRoot "/var/www/html/laravel/public"
        <Directory /var/www/html/laravel/public>
            Options Indexes FollowSymLinks MultiViews
            AllowOverride All
            Order allow,deny
            allow from all
        </Directory>
    </VirtualHost>

    sudo systemctl restart apache2
</code>

6. setup laravel.conf as default configuration
<code>
    sudo a2enmod rewrite
    sudo systemctl restart apache2
    
    sudo a2ensite laravel.conf
    sudo systemctl restart apache2
</code>

7. upload your laravel project
<code>
    sudo git clone
    sudo cp .env.example .env
</code>

8. change permission of laravel project
<code>
    sudo chown -R www-data:www-data /var/www/html/laravel
    sudo chmod -R 775 /var/www/html/laravel
    sudo chmod -R 775 /var/www/html/laravel/storage
    sudo chmod -R 775 /var/www/html/laravel/bootstrap/cache
</code>

# Situational

- install Node.js and npm
<code>
    sudo apt-get install nodejs npm
</code>

- install git
<code>
    sudo apt install git
</code>

- to ignore platform PHP requirements
<code>
    composer install --ignore-platform-reqs
</code>

- restart apache 2 server
<code>
    sudo systemctl restart apache2 | sudo service apache2 restart
</code>

- uninstall all package in php including composer
<code>
    sudo apt-get purge 'php*'
</code>




