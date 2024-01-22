# Docker Commands

Fonte: https://www.youtube.com/watch?v=3c-iBn73dDE&ab_channel=TechWorldwithNana

### Container and image

    Ex: [IMAGE_NAME] = redis
    Ex: [CONTAINER_ID] = d7a6ef66e6da
    Ex: [CONTAINER_NAME] = heuristic_raman

### Pull image from cloud repository

    docker pull [IMAGE_NAME]
    docker pull [IMAGE_NAME]:[IMAGE_VERSION]

### Run image (creating a new container)

    docker run [IMAGE_NAME]
    docker run [IMAGE_NAME]:[IMAGE_VERSION]

### Run image in detached mode (background - terminal session does not get locked)

    docker run -d [IMAGE_NAME]

### Run image with a customized name

    docker run [IMAGE_NAME] --name [NEW_NAME]

### List running containers

    docker ps

### List all containers (running and stopped containers)

    docker ps -a

### List all images that you have locally

    docker images

### Removes an image

    docker rmi [IMAGE_ID/NAME]

### Stops a running container

    docker stop [CONTAINER_ID/NAME]

### Starts a previously created container

    docker start [CONTAINER_ID/NAME]

### Removes a container

    docker rm [CONTAINER_ID/NAME]

### Port binding between host and container

    docker run -p [host_port]:[container_port] [IMAGE_NAME]

### Show logs of a container

    docker logs [CONTAINER_ID/NAME]

### Access interactive terminal of a container

    docker exec -it [CONTAINER_ID/NAME] [SHELL]
    [SHELL] = /bin/bash or /bin/sh

### Check status of running containers

    docker stats

### Copy files to and from a container

    docker cp [SOURCE] [DESTINATION]
    docker cp [HOST_DIR_OR_FILE] [CONTAINER_ID/NAME]:[CONTAINER_DIR]
    docker cp [CONTAINER_ID/NAME]:[CONTAINER_DIR_OR_FILE] [HOST_DIR]

### List docker networks

    docker network ls

### Create a docker network

    docker network create mongo-network

### Filter matches all containers that are connected to a network with a name

    docker ps --filter network=net1

### Inspect container/images

    docker inspect [CONTAINER_ID]
    docker inspect [IMAGE_ID]

### Get an instance’s IP address

    docker inspect --format='{{range.NetworkSettings.Networks}}{{.IPAddress}}{{end}}' [CONTAINER_ID]

### Get an instance’s MAC address

    docker inspect --format='{{range.NetworkSettings.Networks}}{{.MacAddress}}{{end}}' [CONTAINER_ID]

### Start mongodb

    docker run -d \
    -p 27017:27017 \
    -e MONGO_INITDB_ROOT_USERNAME=admin \
    -e MONGO_INITDB_ROOT_PASSWORD=password \
    --net mongo-network \
    --name mongodb \
    mongo

Obs: Check docker compose file of this command (mongo-docker-compose.yaml).

### Start mongo-express (mongodb ui)

    docker run -d \
    -p 8081:8081 \
    -e ME_CONFIG_MONGODB_ADMINUSERNAME=admin \
    -e ME_CONFIG_MONGODB_ADMINPASSWORD=password \
    -e ME_CONFIG_MONGODB_SERVER=mongodb \
    --net mongo-network \
    --name mongo-express \
    mongo-express

Obs: Check docker compose file of this command (mongo-docker-compose.yaml).

### Run a container with environment file

    docker run -d --env-file ./.env [IMAGE_NAME]:[TAG]

### Runa container with privileged permissions (Ex: Mount network share)

    docker run -d --privileged [IMAGE_NAME]:[TAG]

### Mounting volumes for data persistence on Databases

    docker run -v [HOST_DIR]:[CONTAINER_DIR]

### Docker volume locations (named volumes) on Host (.yaml)

   * Windows:    C:\ProgramData\docker\volumes
   * Linux:      /var/lib/docker/volumes

### Creates and starts the containers using a docker compose file (.yaml) on detached mode (-d)

    docker-compose -f mongo-docker-compose.yaml up -d
    
Obs: On docker compose file there is no need to specify network because it creates automatically a new network.

### Build images before creating containers

    docker-compose -f mongo-docker-compose.yaml up -d --build

### Force recreation of containers (similar to a reboot) even if their configuration and image haven't changed

    docker-compose -f docker-compose-prod.yml up -d --force-recreate

### Stops the containers using the docker compose file (.yaml)

    docker-compose -f mongo-docker-compose.yaml down

### Builds an image from a Dockerfile located at the current directory (.)

    docker build -t [NEW_IMAGE_NAME]:[NEW_IMAGE_VERSION] .

### Login on a private Docker Registry (repository) to upload the customized image (you will be prompted for credentials)

    docker login registry.tce.pa
    docker login private.registry.tld:8080

### Logout log out of a Docker Registry (repository)

    docker logout registry.tce.pa
    docker logout private.registry.tld:8080

### Copy an image with another name, the image ID remains the same

    docker tag [IMAGE_NAME]:[IMAGE_VERSION] [REPOSITORY_DOMAIN]/[NEW_IMAGE_NAME]:[NEW_IMAGE_VERSION]
    docker tag my-app:1.0 5468256.eu-central-1.amazonaws.com/my-app:1.0

### Push an image to the provided repository (Docker Registry)

    docker push 5468256.eu-central-1.amazonaws.com/my-app:1.0

### Grants permission to docker commands to a specific linux user

    $ usermod -aG docker [USERNAME]

### Removes all containers

    $ docker rm -f $(docker ps -a -q)

### Removes all volumes

    $ docker volume rm $(docker volume ls)


## Exemplos

### Comando do projeto extracao-doe do Patrick

    docker run --rm -ti -v "/mnt/c/Users/0101119/Google Drive/TCE/Projetos/extracao-doe":/root -p 8000:8501 --entrypoint /bin/bash extracao-doe

### Comando do projeto docx2pdf

    docker run -d --privileged --env-file ./.env docx2pdf:0.5
