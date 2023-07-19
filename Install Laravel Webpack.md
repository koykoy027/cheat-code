## Laravel Webpack installation and commands

1. Install Laravel Jetstream
```
composer require laravel/jetstream
```
```
php artisan jetstream:install livewire
```
```
npm install && npm run dev
```
```
php artisan migrate
```

2. Install Laravel Breeze
```
composer require laravel/breeze--dev
```
```
php artisan breeze:install
```
```
npm install && npm run dev
```
```
php artisan migrate
```

3. Install Laravel and reactjs
```
composer require laravel/ui
```

```
php artisan ui react
```

install react with auth (optional)
```
php artisan ui react --auth
```

## LARAVEL COMMAND
Run specefic db seed base on class
```
php artisan db: seed--class=SpecialOptionTableSeeder
```

CREATE A MODEL AND ITS ASSOCIATED MIGRATION AND CONTROLLER
```
php artisan make:model ModelName - mc
```

CREATE A RESOURCE CONTROLLER WITH CRUD METHODS
```
php artisan make:controller ControllerName--resource
```
CREATES A MIDDLEWARE
```
php artisan make:middleware MiddlewareName
```
RUN SPECEFIC SEEDER CLASS
```
php artisan db: seed--class=SpecialOptionTableSeeder
```
SCAFFOLD BASIC LOGIN AND REGISTRATION VIEWS AND LOGIC
```
php artisan make: auth
```
