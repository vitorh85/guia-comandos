# Docker Commands

### Container and image

    Ex: <image_name> = redis
    Ex: <container_ID> = d7a6ef66e6da
    Ex: <container_name> = heuristic_raman

### Pull image from cloud repository

    docker pull <image_name>
    docker pull <image_name>:<image_version>

### Run image (creating a new container)

    docker run <image_name>
    docker run <image_name>:<image_version>

### Run image in detached mode (background - terminal session does not get locked)

    docker run -d <image_name>

### Run image with a customized name

    docker run <image_name> --name <any_name>

### List running containers

    docker ps

### List all containers (running and stopped containers)

    docker ps -a

### List all images that you have locally

    docker images

### Removes an image

    docker rmi <image_ID/name>

### Stops a running container

    docker stop <container_ID/name>

### Starts a previously created container

    docker start <container_ID/name>

### Removes a container

    docker rm <container_ID/name>

### Port binding between host and container

    docker run -p <host_port>:<container_port> <image_name>

### Show logs of a container

    docker logs <container_ID/name>

### Access interactive terminal of a container

    docker exec -it <container_ID/name> <shell>
    <shell> = /bin/bash or /bin/sh

### Check status of running containers

    docker stats

### Copy files to and from a container

    docker cp <src> <dest>
    docker cp <host_dir_or_file> <container_ID/name>:<container_dir>
    docker cp <container_ID/name>:<container_dir_or_file> <host_dir>

### List docker networks

    docker network ls

### Create a docker network

    docker network create mongo-network

### Filter matches all containers that are connected to a network with a name

    docker ps --filter network=net1

### Inspect container/images

    docker inspect $container_ID
    docker inspect $image_ID

### Get an instance’s IP address

    docker inspect --format='{{range.NetworkSettings.Networks}}{{.IPAddress}}{{end}}' $INSTANCE_ID

### Get an instance’s MAC address

    docker inspect --format='{{range.NetworkSettings.Networks}}{{.MacAddress}}{{end}}' $INSTANCE_ID

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

### Mounting volumes for data persistence on Databases

    docker run -v <host_dir>:<container_dir>

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

    docker build -t <new_image_name>:<new_image_version> .

### Login on a private Docker Registry (repository) to upload the customized image (you will be prompted for credentials)

    docker login registry.tce.pa
    docker login private.registry.tld:8080

### Logout log out of a Docker Registry (repository)

    docker logout registry.tce.pa
    docker logout private.registry.tld:8080

### Copy an image with another name, the image ID remains the same

    docker tag <image_name>:<image_version> <repository_domain>/<new_image_name>:<new_image_version>
    docker tag my-app:1.0 5468256.eu-central-1.amazonaws.com/my-app:1.0

### Push an image to the provided repository (Docker Registry)

    docker push 5468256.eu-central-1.amazonaws.com/my-app:1.0

### Exemplo de comando em um app

    docker run --rm -ti -v "/mnt/c/Users/fulano/Drive/Projetos/extracao":/root -p 8000:8501 --entrypoint /bin/bash extracao

### Grants permission to docker commands to a specific linux user

    $ usermod -aG docker <username>

### Removes all containers

    $ docker rm -f $(docker ps -a -q)

### Removes all volumes

    $ docker volume rm $(docker volume ls)