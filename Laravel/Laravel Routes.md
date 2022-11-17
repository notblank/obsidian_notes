```
Route::get('/route_name', function () {
    return view('welcome');
});
```

- Usually routes return a view
-  /route_name runs the function

#### Parameters

Are written {param_name} inside route. Then, they are caught by the function in php.

```
Route::get('/route_name/{param_name}', function ($param_name) {
    return $param_name;
});
```

For multiple parameters

```
{p1}/{p2}/....
``` 

#### Naming routes

Naming route inside  php callback function.

Wrap function in a dictionary (associative arary):

```
Route::get('/old_name', array('as' => 'new_name', function () {

}));
```

To get all routes:

```
> php artisan route:list
```
