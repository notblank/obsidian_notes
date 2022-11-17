Contents:
- Versioning images
- Sharing images
- Saving and loading images
- Reducing the image size
- Speeding up builds

## Images and Containers

The image everything needed to run an application:
- An os
- libraries
- app files
- env vars
- ...

The container is like a VM. It's an isolated environment to run the app. It's a process.

__Can run many containers from an image.__

## Building an image

Choose os and env. Look in docker hub/ samples

```
FROM OS
ENV env
```

Build Image:

```
docker build -t image_name path_to_dockerfile
```

Start container 

```
docker run -it image_name
```

## Copy Files and Directories

```
COPY current_dir image_dir
```

Can use relative paths by adding

```
WORKDIR /image_dir
```

Can also use 

```
ADD
```

can add files from url and compressed files (they get uncompressed).

Copy is preferred

## Excluding Files and Directories

Exclude some directories to build them then once the image is transferred. 

Use .dockerignore

## Running Commands

```
RUN terminal_command 
```

## Setting Environment Variables

```
ENV VAR_NAME=var_value
```

## Exposing Ports

Running an app in a container opens ports in the container. To document this use:

```
EXPOSE 3000
```

## Setting the User

1. Create a group.
2. Add a user and put him in the group.
3. Check the user. 

```
addgroup group_name && adduser -S -G user_name group_name
```

Run the command and change the user 

```
RUN create group && create user in group
USER user_name 
```

## Defining Entry Points


## CMD 

Executed while starting a container.

To run:

```
docker run cmd  by writing docker run 
```

In Dockerfile

(Shell form)
exec inside a separate shell

```
CMD cmd
```

(Exec form)
exec directly, same shell
This is preferred

```
CMD ['npm', 'start']
```


## Entrypoint

Similar to CMD. 

Two forms exec and shell froms.
Entrypoint is harder to override. To override CMD just write andother CMD below.

```
ENTRYPOINT ['npm', 'start']
```


## Speeding Up Builds

Image = collection of layers
layer = modified files

To see layers:

```
docekr history image_name
```

__Optimization:__
If nothing changed, use old layer.
Once a layer is rebuilt all following layers are rebuilt.
Idea: separate copy files from installing dependencies.

Cange:

```
COPY . .
RUN cmd_name 
```

To:

```
COPY files_needed_to_run cmd_name
RUN cmd_name
COPY . . 
```

Ideally order Dockerfile:

```
Stable Instructions
	|
	to
	|
Changing Instructions
```

## Removing Images

Remove containers

```
docker container prune
```

then, remove dangling images

```
docker image prune
```

To remove an image

```
docker image rm image_name or image_id
```

## Tagging Images

Label image for easy identification.

Use -t tag flag while building:

```
docker build -t img_name:tag_name
```

Same images with multiple tags. Remove img_name:tag_name 

Can also use tag command:

```
docker image tag img_name:tag_name
```

## Sharing Images

Same as with github

Log in

```
docker login
```

Then, push:

```
docker push docker_hub_user_name/repo_name:tag_name 
```

Pull from docker hub


## Saving and Loading Images

Save as compressed file to load in another machine.

```
docker image save -o output_file.tar image_name:tag_name
```

File contains the layers.

To load

```
docker image load img_file.tar 
```