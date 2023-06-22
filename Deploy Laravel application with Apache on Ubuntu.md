# Deploy Laravel application with Apache on Ubuntu

1. update ubuntu first

    'sudo apt-get update
    sudo apt-get install apache2'

2. this is optional, only run if the php requirements are <= 8.2.6
sudo add-apt-repository -y ppa:ondrej/php 
sudo apt-get update

3. install all php package
sudo apt install php php-cli php-mbstring php-xml php-zip php-mysql composer

4. search and change ;cgi.fix_pathinfo=1 into cgi.fix_pathinfo=0
sudo nano /etc/php/8.2/apache2/php.ini
sudo nano /etc/php/8.2/cli/php.ini

5. setup customize configuration
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

6. setup laravel.conf as default configuration
sudo a2enmod rewrite
sudo systemctl restart apache2

sudo a2ensite laravel.conf
sudo systemctl restart apache2

7. upload your laravel project
sudo git clone
sudo cp .env.example .env


8. change permission of laravel project
sudo chown -R www-data:www-data /var/www/html/laravel
sudo chmod -R 775 /var/www/html/laravel
sudo chmod -R 775 /var/www/html/laravel/storage
sudo chmod -R 775 /var/www/html/laravel/bootstrap/cache

# Situational

1. install Node.js and npm
sudo apt-get install nodejs npm

2. install git
sudo apt install git

3. to ignore platform PHP requirements
composer install --ignore-platform-reqs

4. restart apache 2 server
sudo systemctl restart apache2 | sudo service apache2 restart

5. uninstall all package in php including composer
sudo apt-get purge 'php*'



