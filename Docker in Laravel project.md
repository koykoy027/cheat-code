<ol>
  <li>Create a Dockerfile: In the root of your Laravel repository (without any file extension)</li>
  <code>
  #Base image
  FROM php:8.2-fpm
    
  #Set working directory
  WORKDIR /var/www/html

  #Install dependencies
  RUN apt-get update && apt-get install -y \
      libonig-dev \
      libxml2-dev \
      libzip-dev \
      unzip \
      curl \
      supervisor

  #Install PHP extensions
  RUN docker-php-ext-install pdo_mysql mbstring exif pcntl bcmath opcache zip

  #Install Composer
  RUN curl -sS https://getcomposer.org/installer | php -- --install-dir=/usr/local/bin --filename=composer

  #Copy application files
  COPY . .

  # Set file permissions
  RUN chown -R www-data:www-data /var/www/html/storage /var/www/html/bootstrap/cache

  # Install dependencies using Composer
  RUN composer install --no-interaction --optimize-autoloader --no-scripts

  # Set up supervisor
  COPY .github/workflows/supervisord.conf /etc/supervisor/conf.d/supervisord.conf

  # Expose port 9000
  EXPOSE 9000

  # Run supervisor
  CMD ["/usr/bin/supervisord", "-c", "/etc/supervisor/conf.d/supervisord.conf"]</code>
</ol>

2. Create a supervisor configuration: In the .github/workflows directory, create a file named supervisord.conf and add the following content
<code>
  [program:laravel-worker]
  process_name=%(program_name)s_%(process_num)02d
  command=php /var/www/html/artisan queue:work --sleep=3 --tries=3
  autostart=true
  autorestart=true
  user=www-data
  numprocs=1
  redirect_stderr=true
  stdout_logfile=/var/www/html/storage/logs/worker.log
</code>

3. Create a GitHub Actions workflow: In the .github/workflows directory, create a file named laravel.yml (or any name ending with .yml) and add the following content
<code>
name: Laravel CI

on:
  push:
    branches:
      - master

jobs:
  laravel:
    runs-on: ubuntu-latest

    services:
      mysql:
        image: mysql:8.0
        env:
          MYSQL_ROOT_PASSWORD: password
          MYSQL_DATABASE: laravel
        ports:
          - 3306:3306
        options: --health-cmd="mysqladmin ping" --health-interval=10s --health-timeout=5s --health-retries=3

    steps:
      - name: Checkout code
        uses: actions/checkout@v2

      - name: Set up Docker
        uses: docker/setup-buildx-action@v1

      - name: Copy .env
        run: cp .env.example .env

      - name: Install Composer dependencies
        run: composer install --no-interaction --optimize-autoloader

      - name: Generate key
        run: php artisan key:generate

      - name: Run tests
        run: php artisan test

</code>


