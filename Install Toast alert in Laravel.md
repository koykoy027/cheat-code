# Install CodeSeven Toastr
1. Install using npm
```
npm install --save toastr
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
