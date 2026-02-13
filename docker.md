# <u>IMAGES </u>
## List all Local images
```bash
docker images
```

## Delete an images
Before going to delete an image,,containers have to be deleted
```bash
docker rmi <images_name>
```

## Remove unused images
```bash
docker image prune
```


## Build an image from a Dockerfile
```bash
docker build -t <image_name>:<version>  # version is optional
docker build -t <image_name>:<version>  #  -no-cache //build without cache
```



</br></br>

# <u>CONTAINER </u> 
## List all Local containers (running & stopped both)
```bash
docker ps -a
```

## List all running containers
```bash
docker ps
```

## Create & run a new container
```bash
docker run <image_name>
# if image not available locally, it’ll be downloaded from DockerHub
docker run -d -e MYSQL_ROOT_PASSWORD=my-secret --name mysql-latest mysql
# This command runs a MySQL database container in the background with a required root password.
```

## Run container in background
```bash
docker run -d <image_name>
```

## Run container with custom name
```bash
docker run - -name <container_name> <image_name>
```

## Set environment variables in a container
```bash
docker run -e <var_name>=<var_value> <container_name> (or <container_id)
```

## Start or Stop an existing container
```bash
docker start|stop <container_name> (or <container_id)
```
## Inspect a running container

```bash
docker inspect <container_name> (or <container_id)
```

## Delete a container
```bash
docker rm <container_name> (or <container_id)   # Docker won’t remove it unless you stop
```


</br></br>

# <u> Port Binding in container</u>
host port -> connect with just one container_port
```bash
docker run -p<host_port>:<container_port> <image_name>
```


</br></br>

# <u>DOCKER HUB</u>
## Pull an image from DockerHub
```bash
docker pull <image_name>
```

## Publish an image to DockerHub
```bash
docker push <username>/<image_name>
```

## Login into DockerHub
```bash
docker login -u <image_name></br>
# Or
docker login
# also, docker logout to remove credentials

```

## Search for an image on DockerHub
```bash
docker search <image_name>
```


</br></br>

# Troubleshoot Commands
It helps us to find any errors in any Container
```bash
# Fetch logs of a container
docker logs <container_name> (or <container_id)

# Open shell inside running container then ->ls then -> env
docker exec -it <container_name> /bin/bash
docker exec -it <container_name> sh
```


</br></br>

# Docker Volumes
Volumes are persistent data stores implemented by the container engine. 
## List all Volumes
```
docker volume ls
```
## Create new Named volume
```
docker volume create <volume_name>
```
## Delete a Named volume
```bash
docker volume rm <volume_name>
```
## Mount Named volume with running container
```bash
docker run - -volume <volume_name>:<mount_path>

# or using - -mount
docker run - -mount type=volume,src=<volume_name>,dest=<mount_path>
```
## Mount Anonymous volume with running container
```bash
docker run - -volume <mount_path>
```
## To create a Bind Mount
```bash
docker run - -volume <host_path>:<container_path>
# or using - -mount
docker run - -mount type=bind,src=<host_path>,dest=<container_path>
```

## Remove unused local volumes
```bash
docker volume prune # for anonymous volumes
```

# <u>Network</u>
## List all networks
```bash
docker network ls
```
## Create a network
```bash
docker network create <network_name>
```
## Remove a network
```bash
docker network rm <network_name>
```

## Remove all unused networks
bash```
docker network prune
```