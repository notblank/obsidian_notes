## What is Docker?

A plataform for building, running and shipping applications.

Avoid:
- misisng files.
- different versions.
- different configurations.

## VM vs Containers

__Container:__ Isolated evironment for running an application.
__VM:__ Abstraction of a machine. Uses hypervisor (virtualbox, vmware).

Some problems with vms:
- need full copy of an OS.
- resource intensive. Use machine resources.

Containers:
- same isolation.
- more lightweight.
- same OS.
- less hardware resources.


## Docker Architecture 

```
Client ---Rest API--> Server
```

Server (Docker Engine) Builds and runs Containers.

All containers share the core of the OS. 

## Development Workflow  

1. Build application.
2. Add dockerfile.
3. Docker packages App into an Image.
4. Load image into container.
5.  Can push image to registry. Then someone can pull image.

## Docker in Action

Create app.js. 

To run need to:
1. Start with an OS.
2. Install Node.
3. Copy app files.
4. Run node app.js

Write instruction in a Dockerfile

```
FROM base_image
COPY app_files /folder_image
CMD execute_cmd /folder_image/file
```

To build the image:

```
docker build -t image_name Dockerfile
```

For a list of images:

```
docker images
```

To run image:

```
docker run image_name
```

To pull images:

```
docker pull image_name
```

and run with docker.

## Starting a Container

-i to interact

```
docker start -i container_id
```

Can login as user 

```
docker exec -it user_name container_id bash
```