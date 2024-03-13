# Full guide in Reactjs in Laravel project using inertiajs

## Installation using vite plugins, and react-router-dom, and tailwindcss

<details>
<summary>
    <b>Server-side setup</b>
</summary>
<br />
     
1. **First, install the Inertia server-side adapter using the Composer package manager.**

```
composer require inertiajs/inertia-laravel
```

2. **Root template**
<p>
    Next, set up the root template that will be loaded on the first-page visit to your application <code>resources/views/app.blade.php</code>. This will be used to load your site assets (CSS and JavaScript), and will also contain a root in which to boot your JavaScript application.
</p>


        
```
<!DOCTYPE html>
<html lang="en">
  <head>
    <meta charset="utf-8" />
    <meta name="viewport" content="width=device-width, initial-scale=1.0, maximum-scale=1.0" />
    @vite('resources/js/app.js')
    @inertiaHead
  </head>
  <body>
    @inertia
  </body>
</html>
```

3. **Middleware**
<p>
Next, we need to set up the Inertia middleware. You can accomplish this by publishing the <code>HandleInertiaRequests</code> middleware to your application, which can be done using the following Artisan command.
</p>

```
php artisan inertia:middleware
```

<p>
Once the middleware has been published, register the <code>HandleInertiaRequests</code> middleware in your <code>App\Http\Kernel</code> as the last item in your web middleware group.
</p>

```
'web' => [
    // ...
    \App\Http\Middleware\HandleInertiaRequests::class,
],
```

</details>


<details>
<summary>
    <b>Client-side setup</b>
</summary>
<br />

1. **Install dependencies - Install inertia, vite, and router**
<p>
First, install the Inertia client-side adapter corresponding to your framework of choice.
</p>

```
npm install @inertiajs/react @vitejs/plugin-react react-router-dom
```

2. **Initialize the Inertia app**
<p>
Next, update your main JavaScript file to boot your Inertia app. To accomplish this, we'll initialize the client-side framework with the base Inertia component <code>resources/js/app.jsx</code>.
</p>

```
import { createInertiaApp } from '@inertiajs/react'
import { createRoot } from 'react-dom/client'

createInertiaApp({
  resolve: name => {
    const pages = import.meta.glob('./Pages/**/*.jsx', { eager: true })
    return pages[`./Pages/${name}.jsx`]
  },
  setup({ el, App, props }) {
    createRoot(el).render(<App {...props} />)
  },
})
```

3. **Install Styled Components** 

```
npm install styled-components
```

</details>

<details>
    <summary>
        <b>TailwindCSS setup</b>
    </summary>
    <br />
</details>

## Simple CRUD 



























