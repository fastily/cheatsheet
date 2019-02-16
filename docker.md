## docker container
```bash
# show running containers
docker container ls # old way was docker ps

# show *all* containers, running or stopped
docker container ls -a

# start container and route traffic from 8080 on the host to 80 on the container.  
docker container run --publish 8080:80 --detach --name '<OPTIONAL_NAME>' '<IMAGE_NAME>'

# stop a running container
docker container stop '<CONTAINER_ID>' # unique prefix of CONTAINER_ID also works

# show logs for a container
docker container logs '<CONTAINER_ID_OR_NAME>'

# view processes running in a container
docker container top '<CONTAINER_ID>'

# (forcibly) remove a cotnainer
docker container rm -f '<CONTAINER_ID>'
```


## misc
```bash
# get version/check that docker is working
docker version
```

