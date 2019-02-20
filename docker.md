## container
```bash
# show running containers
docker container ls # old way was docker ps

# show *all* containers, running or stopped
docker container ls -a

# start container and route traffic from 8080 on the host to 80 on the container.  
docker container run --publish 8080:80 -d --name '<OPTIONAL_NAME>' '<IMAGE_NAME>'

# start container and attach it to the specified network 
docker container run -d --network '<NETWORK_ID>' --name '<OPTIONAL_NAME>' '<IMAGE_NAME>'

# start container with specified network and DNS alias.  Can be used for round-robin DNS
docker container run -d --network '<NETWORK_ID>' --network-alias '<ALIAS_NAME>' '<IMAGE_NAME>'

# stop a running container
docker container stop '<CONTAINER_ID>' # unique prefix of CONTAINER_ID also works

# show logs for a container
docker container logs '<CONTAINER_ID_OR_NAME>'

# view processes running in a container
docker container top '<CONTAINER_ID>'

# (forcibly) remove a cotnainer
docker container rm -f '<CONTAINER_ID>'

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

## iamge
```bash
# list downloaded images
docker image ls

# show image layers/history
docker image history '<IMAGE_NAME>'

# 

```



## misc
```bash
# get version/check that docker is working
docker version
```

