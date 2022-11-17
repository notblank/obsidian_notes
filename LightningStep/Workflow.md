1. pull from develop.
2. checkout to ticket branch.
3. run local server:

``` 
vagrant up
```

4. connect to the virtual machine:

```
vagrant ssh
```

	1. install php dependencies: composer install
	2. update databases: php artisan migrate 
	3. update routes: php artisan optimize
