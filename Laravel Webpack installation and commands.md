# Laravel Webpack installation and commands

1. Install Laravel Jetstream
```
composer require laravel / jetstream
php artisan jetstream:install livewire
npm install && npm run dev
php artisan migrate
```
2. Install Laravel Breeze
```
composer require laravel / breeze--dev
php artisan breeze: install
npm install && npm run dev
php artisan migrate
```
3. Install Flowbite tailwindcss
```
npm install - D tailwindcss postcss autoprefixer flowbite
npx tailwindcss init - p
```

open tailwind.config.js
```
module.exports = {
	content: [
		"./resources/**/*.blade.php",
		"./resources/**/*.js",
		"./resources/**/*.vue",
		"./node_modules/flowbite/**/*.js"
	],
	theme: {
		extend: {},
	},
	plugins: [
		require('flowbite/plugin')
	],
}
```

### open app.css and paste
```
@tailwind base;
@tailwind components;
@tailwind utilities;

@vite(['resources/css/app.css', 'resources/js/app.js'])
```

### open app.js and paste
```
import 'flowbite';
```

4. Install CodeSeven Toastr
```
npm install--save toastr
```

### open app.js and paste
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

### open app.scc and paste
```
@import '../../node_modules/toastr/toastr.scss';
import 'toastr/toastr.scss';
```
### how to apply in blade

```
@if (session('status') === 'password-updated')
	<script>
		document.addEventListener('DOMContentLoaded', function() {
			toastr.success('Your password has been successfully updated.');
		});
	</script>
@endif
```

LARAVEL COMMAND
```php artisan db: seed--class=SpecialOptionTableSeeder


SHORTCUT COMMANDS
CREATE A MODEL AND ITS ASSOCIATED MIGRATION AND CONTROLLER `php artisan make:model ModelName - mc`
CREATE A RESOURCE CONTROLLER WITH CRUD METHODS `php artisan make:controller ControllerName--resource`
CREATES A MIDDLEWARE `php artisan make:middleware MiddlewareName`
RUN SPECEFIC SEEDER CLASS `php artisan db: seed--class=SpecialOptionTableSeeder`


SCAFFOLD BASIC LOGIN AND REGISTRATION VIEWS AND LOGIC `php artisan make: auth`
