resources/views

A view is a template. Render a view using a controller.

```
Route::get('/route_name', 'ControllerName@method')
```

The method:

```
public function method_name() {
	return view('view_name')
}
```

returns the view 

```
resources/views/ view_name
```

### Pass Data Into Views

Retreive the data from the route 

```
Route::get('route_name/{var_name}', 'Controller_Name@method')
```

Then, on the method return the view with the variable:

```
public function method ($id) {
	return view('view_name')->with('var_name', $var_name);
	// equivanlently:
	// easier for more variables
	// view('view_name', compact('id', 'var2', ...))
}
```

Finally, use the variable in the view:

```
{{ $var_name }}
```
