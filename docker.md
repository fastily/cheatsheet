## container
```bash
# show running containers
docker container ls # old way was docker ps

# show *all* containers, running or stopped
docker container ls -a

# start container and route traffic from 8080 on the host to 80 on the container.  
docker container run -d --publish 8080:80 --name '<OPTIONAL_NAME>' '<IMAGE_NAME>'

# start container and attach it to the specified network 
docker container run -d --network '<NETWORK_ID>' --name '<OPTIONAL_NAME>' '<IMAGE_NAME>'

# start container with specified network and DNS alias.  Can be used for round-robin DNS
docker container run -d --network '<NETWORK_ID>' --network-alias '<ALIAS_NAME>' '<IMAGE_NAME>'

# start container with a specified volume name and path
docker container run -d -v '<OPTIONAL_NAME>':'<MOUNT_PATH_ON_CONTAINER>' '<IMAGE_NAME>'

# start container and bind mount it to the specified path
docker container run -d -v '<PATH_TO_LOCAL_DIRECTORY>':'<MOUNT_PATH_ON_CONTAINER>' '<IMAGE_NAME>'

# stop a running container
docker container stop '<CONTAINER_ID>' # unique prefix of CONTAINER_ID also works

# show logs for a container
docker container logs '<CONTAINER_ID_OR_NAME>'

# view processes running in a container
docker container top '<CONTAINER_ID>'

# (forcibly) remove a cotnainer
docker container rm -f '<CONTAINER_ID>'

# remove all stopped containers
docker rm $(docker ps -a -q)

# show json metadata about container (startup config, volumes, networking, etc)
docker container inspect '<CONTAINER_ID>'

# show live performance for all containers
docker container stats 

# create a container and start an interactive shell in it
docker container run -i -t '<IMAGE_NAME>' bash

# create a container, start an interactive shell in it, delete the container on exit
docker container run --rm -i -t '<IMAGE_NAME>' bash

# run a stopped container and start an interactive shell in it
docker container start -a -i '<CONTAINER_ID>'

# start a shell in a running container
docker container exec -i -t '<CONTAINER_ID>' bash

# view port mappings for a container
docker container port '<CONTAINER_ID>'
```

## network
```bash
# show networks
docker network ls

# get json metadata about a network
docker network inspect

# create a network (w/ default bridge driver)
docker network create '<NAME>'

# create a network with the specified network driver
docker network create --driver '<DRIVER_ID>' '<NAME>'

# add container to a network (like installing a new NIC and connecting to ethernet)
docker network connect '<NETWORK_ID>' '<CONTAINER_ID>'

# remove a network from a container
docker network disconnect '<NETWORK_ID>' '<CONTAINER_ID>'
```

## image
```bash
# list downloaded images
docker image ls

# show image layers/history
docker image history '<IMAGE_NAME>'

# json metadata about an image
docker image inspect '<IMAGE_NAME>'

# give a new tag to an existing image
docker image tag '<IMAGE_NAME>':'<OPTIONAL_TAG_NAME>' '<USERNAME>'/'<IMAGE_NAME>':'<OPTIONAL_TAG_NAME>'

# upload changed layers to docker hub
docker image push '<REPOSITORY>':'<OPTIONAL_TAG_NAME>'

# build an image based on a dockerfile 
docker image build -t '<TAG_NAME>' '<DIRECTORY_TO_BUILD_IN>'

# remove an image from the cache
docker image rm '<IMAGE_ID>'

# remove all images without at least one associated container
docker image prune -a
```

## volume
```bash
# list volumes
docker volume ls

# delete unused local volumes
docker volume prune -f
```

## dockerfile
```Dockerfile
# create a new volume location and assign it to this location in the container.  Outlives container
VOLUME PATH/TO/DIRECTORY
```

## docker-compose
```bash
# setup all volumes/networks and start containers, run detached
docker-compose up -d

# stop all containers and remove containers/volumes
docker-compose down -v

# (re)build all custom images
docker-compose build

# view logs
docker-compose logs

# view containers, running and stopped
docker-compose ps

# view running processes
docker-compose top
```

## swarm
```bash
# list running swarm nodes
docker node ls

# create a service/container and run a command
docker service create '<IMAGE_NAME>' '<COMMAND_TO_RUN>'

# list running services/containers
docker service ls

# list tasks for a service
docker service ps '<CONTAINER_ID>'

# scale up a service to 3 instances
docker service update '<SERVICE_ID>' --replicas 3

# remove a service
docker service rm '<SERVICE_NAME>'

```

## misc
```bash
# get version/check that docker is working
docker version

# login to push
docker login

# logout
docker logout

# enable swarm
docker swarm init
```