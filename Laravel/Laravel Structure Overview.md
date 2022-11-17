Description of folders inside project:

- /app 
	- folder contains models and controllers
- /bootstrap start app
- /configuration 
	- all configs, database, mail, views, sessions, ...
- /database 
	- migrations to create tables and files.
- /public 
	- public files, css, js, index.php, htaccess, ...
- /resources 
	- files compilation with webpack, languages, __views__
	- compiled files go to /public 
- /routes
	- web.php principal file 
- /vendor composer file
	- /vendor/.env contains all sensitive info, not pushed
	- /vendor/artisan generate tables, controllers, models  
	