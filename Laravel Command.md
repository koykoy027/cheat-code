### LARAVEL COMMAND
- **Run specific db seed based on class**
```
php artisan db: seed --class=SpecialOptionTableSeeder
```

- **CREATE A MODEL AND ITS ASSOCIATED MIGRATION AND CONTROLLER**
```
php artisan make:model ModelName - mc
```

- **CREATE A RESOURCE CONTROLLER WITH CRUD METHODS**
```
php artisan make:controller ControllerName --resource
```

- **CREATES A MIDDLEWARE**
```
php artisan make:middleware MiddlewareName
```

- **SCAFFOLD BASIC LOGIN AND REGISTRATION VIEWS AND LOGIC**
```
php artisan make: auth
```

- **CONVERT DATE TO FORMAT**
<p>If you want to format the date as <code>July 2023</code> , you can use the following code</p>

```
{{ \Carbon\Carbon::parse($data->birthday)->format('F Y') }}
```

<p>If you want to format the date as <code>July 27, 2000</code> , you can use the following code</p>

```
{{ \Carbon\Carbon::parse($data->birthday)->format('F d, Y') }}
```
