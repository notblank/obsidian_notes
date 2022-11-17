- Starting/Stoping
- Publishing ports
- Viewing logs
- Executing commands in containers
- Removing containers
- Persisting data using volumes
- Sharing source code

## Starting Containers

To see containers use the ps = process command

To run a container using:
- -d = detatched flag.
- --name to name container

```
docker run -d --name container_name img_name
```

## Viewing the Logs

Look inside a container.

```
docker logs conatainer_id
```

- can use --help for options

## Publishing Ports

Access ports of the container from local computer

```
docker run -p host_port:container_port img_name
```

## Executing Commands in Running Containers

```
docker exec container_name cmd
```

 To run bash 
 
```
docker exec -it container_name bash
```

## Stoping and Starting Containers

```
docker stop container_name
```


## Removing Containers

```
docker container rm container_name
```

## Container File System

Data in container is deleted with it. Use volumes for persisting data.

## Persisting Data using Volumes

Volume - storage outside containers

```
docker volume
```

To run a container with a volume use -v tag

```
docker run ... -v vol_name:container_dir
```

The vol_name or container_dir are created if they don't exist.  Dirs and files created are owned by root by dafault.

Create directory in Dockerfile.

## Copying Files between Host and Containers


```
docker cp container_name:path/file_container host_dir 
```

To copy from host to container just change the order above 

## Sharing the Source Code with a Container

Update local changes on the container.

For development: can map a dir in host to a dir in a container. Changes are immediatly visible

Use -v flag in the run:

```
docker run -d -p 5001:3000 -v $(pwd):container_dir
```

obs:
- To add volume add another -v flag.
