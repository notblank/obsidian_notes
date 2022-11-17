Located at

```
/app/http
```

To declare a namespace

namespace = Scope of functions used inside controllers

```
namespace App\http\Functions;
```

use import classes, functions, namespaces, etc

#### Creating Controllers

```
> php artisan make:controller ControllerName
```

Creates 

```
App/Http/Controllers/ControllerNam.php
```

- use --resource for extra code inside

#### Routing Controllers

 In a route:
 
```
Route::get('/route_name', '\local_path_to_controller\ControllerName@Method');
```

Obs: 
- path to controller with \

##### To pass data:

```
Route::get('/{data}', '\path\ControllerName@Method');
```

And use inside the controller 

```
Method ($data)
```

#### Resources and Controllers

```
Route::resource('/route', 'ControllerName');
```

Creates routes for all --resource flag related methods.