Contents:
- Docker Compose
- Docker networking
- Database migration
- Running automated tests

## Installing Docker Compose

```
docker-compose --version
```

## Cleaning Up our Workspace

```
docker ... rm $( cmd to list all containers )
```

## The Sample Web Application

Need 3 containers:

- Frontend
- Backend 
- Database

In Docker to do all of this run:

```
docker-comopse up
```

in the directory with the docker-compose.yml file.


## JSON and YAML Formats

JSON: readable language for representing data. List of key-value pairs.
YAML: like JSON with less clutter.

```
---
key1: value1
# lists
key2: 
	- val21
	- val22
# objects
key3:
	key31: val31
	key32: val32
```

Parsing YAML is a slower than JSON.

	YAML for config and JSON for computers.

## Creating Compose File

Needs to be called docker-compose.yml

```
version: "3.8"
services:
	service_name1:
		# build images
		build: path_to_Dockerfile_of_service
		ports:
			- port_host:port_container
		environment:
			- ENV_VAR=value
			# can also use object sintax
			ENV_VAR: value
	service_name2:
		# to pull images from docker hub
		image: name_of_image_on_dockerhub 
		ports:
			- special ports for databases/ use the same ports
		volumes:
			- vol_namme:dir_in_container
			
# Define volume before using it above
volumes:
	vol_name:
```

Obs
- DB_URL var tells where the db is. 

```
  host_name: 
    build: ./backend
    ports: 
      - 3001:3001
    environment:
      DB_URL: mongodb://host_name/data_base_name
```

## Building Images

docker-compose is built over docker engine. Sole difference is that commands are applied to every container/services in app.

```
docker-compose build
```


## Starting and Stoping the Application

```
docker-compose up/down
```


## Docker Networking

Docker-compose creates a network of containers. They can talk to each other.

```
docker network
```

DNS server with name and ip of containers. Each container contains the dns resolver. The resolver gathers info from the server.

## Viewing Logs

```
docker-compose logs
```

## Publishing Changes

To avoid rebuilding after every change.

```
volumes: 
	- ./local_dir:/container_app
```

Obs:
- May have errors if local dir does not contain dependencies.

## Migrating the Database

Populate the database with specific data before deploying.

Inside the docker-compser.yml file:

```
command: ./wait-for wait_for_container:port && migrate ...
```

To wait for data base container and then, migrate.

If script is too long you can store in a .sh script and type

```
command: ./entrypoint.sh 
```
