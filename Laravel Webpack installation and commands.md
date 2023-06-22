## Laravel Webpack installation and commands

1. Install Laravel Jetstream
```
composer require laravel / jetstream
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
composer require laravel / breeze--dev
```
```
php artisan breeze: install
```
```
npm install && npm run dev
```
```
php artisan migrate
```


## Install CodeSeven Toastr
1. Install using npm
```
npm install--save toastr
```

2. open resources/js/app.js and paste
```
import toastr from 'toastr';
toastr.options = {
	"closeButton": false,
	"progressBar": false,
	"positionClass": "toast-top-right",
	"showDuration": "300",
	"hideDuration": "1000",
	"timeOut": "5000",
	"extendedTimeOut": "1000",
	"showEasing": "swing",
	"hideEasing": "linear",
	"showMethod": "fadeIn",
	"hideMethod": "fadeOut"
};

// Make toastr available to all components
window.toastr = toastr;
```

2. open resources/css/app.css and paste
```
@import '../../node_modules/toastr/toastr.scss';
import 'toastr/toastr.scss';
```

3. how to apply in blade
```
@if (session('status') === 'password-updated')
	<script>
		document.addEventListener('DOMContentLoaded', function() {
			toastr.success('Your password has been successfully updated.');
		});
	</script>
@endif
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
