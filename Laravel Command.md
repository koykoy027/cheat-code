### LARAVEL COMMAND
- **Run specific db seed based on class**
```
php artisan db: seed--class=SpecialOptionTableSeeder
```

- **CREATE A MODEL AND ITS ASSOCIATED MIGRATION AND CONTROLLER**
```
php artisan make:model ModelName - mc
```

- **CREATE A RESOURCE CONTROLLER WITH CRUD METHODS**
```
php artisan make:controller ControllerName--resource
```

- **CREATES A MIDDLEWARE**
```
php artisan make:middleware MiddlewareName
```

- **RUN SPECEFIC SEEDER CLASS**
```
php artisan db: seed--class=SpecialOptionTableSeeder
```

- **SCAFFOLD BASIC LOGIN AND REGISTRATION VIEWS AND LOGIC**
```
php artisan make: auth
```

- **CONVERT DATE TO FORMAT MONTH YEAR**
> eg. July 2023
```
{{ \Carbon\Carbon::parse($newEducationalAttainment->period_of_attendance_from)->format('F Y') }}
```
