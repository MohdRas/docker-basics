#  docker-basics

BASICS
# What is Container & docker
  - container has its own isolated environment ( application + dependencies + configuration)
    - With containers, no need to install any application directly on OS.
    - One commmand to fetch the image & start the container.
    - docker run postgres:9.6 -->> download + run an image->> postgres:9.6 => name of the image:version
      - find first image LOCALLY ( on the host ) ->> if not found then download it from docker hub.
      - Different versions of the image can be downloaded and run on the same host ( local machine )
      - each layer of the image is downloaded separately.
      - Downloading two versions of the same image
        - After downloading first version, if we download second version, then the layers which are present LOCALLY, won't be downloaded again. 
  - docker image vs docker container
    - docker image is the one which actually reside on repository ( docker hub )
    - docker image is the portable/movable arftifact.
    - docker image is pulled and started on my local machine (host)
      - it is now "a container running on my local machine".
      - it creates a container environment.
  - With Containers, development & operations team work together, to package an application in a container with all its dependencies & configuration.
  - Deployment before containers - 
    - Portable actifact(JAR/WAR + Database service + Instructions ). 
    - Development team give the Portable actifact to the Operations team. Operations team deploy the application.
    - Dependency versions conflicts.
    - Misunderstanding between development & operations team.
    - Textual guide for deployment about External Dependencies, instructions & configurations.
  - Development & deployment improvement
    - Development improvement 
      - No need to follow different instructions to install applications ( DB ) for each OS & Application.
    - Deployment imporovement 
      - No need to share steps to deploy it along with its artifact, dependencies and configuration.
  - Where to store these images? 
    - image repository is used to store images.
  - Private repository of images. 
    - Companies have their own private repository for their own images.
  - Public Repository ( DockerHub ) for Docker images 
    - Only docker images can reside.
    - Official & non-official container images ( Jenkins ) .
   
  - Layers of a image
    - base image ->> intermediate image ->> application image
    - base image layer (Linux based image - small in size ) - basic OS & dependencies
    - dependency layer - library + framework
    - code layer - code + configuration
    - build layer - tools & scripts to compile the application
    - run layer - runtime dependencies + configuration

  # Docker vs VM.
  - Both are virtualization tools.
  - What part of OS, Docker virtualize ?
    - Docker virtualize the Applications layer and uses the Kernel of the Host machine.
    - Size -->> Docker image smaller than VM
    - Speed ->> Docker containers start & run faster than VM
    - Compatibility -->> VM of any OS can run on any Host OS.
  - What part of OS, VM virtualize ?
    - VM virtualizes the applications layer and OS Kernel layer. 
    - it virtualizes the complete OS layer (OS Kernel + Applications).
  - OS architecture ( Hardware -> OS -> Software Applications (Excel) )
  - Layers of any OS
    - Applications layer 
      - run on OS Kernel Layer
    - OS Kernel layer 
      - communicate with Hardware ( CPU + MEMORY )
    - Hardware laqyer
      - CPU + MEMORY
    - Running Linux based image might not be compatible on windows host ( Windows Kernel + Windows Applications ) 
      - it is true for windows version < 10 and old mac versions.
      - This problem can be solved through WSL2 ( WINDOWS SUB SYSTEM FOR LINUX ). It is Linux-based Kernel inside VM of Windows.
      - This means Linux image is not directly running on windows kernel, rather on the Linux kernel inside windows VM.
      - Windows kernel can not run Linux based image natively
      - Docker ToolBox(Legacy Solution) is used to run any OS based image on any Host OS.
# Docker installation.
- Installation will differ for each OS and its version.
- Install docker on Windows/Mac/Linux
- Community Edition ( CE ) & Enterprise Edition ( EE ) 
- Prerequisites ( System Requirements )
  - OS version & Hardware criteria (RAM)
  - Installation includes - DOCKER ENGINE, DOCKER CLI, DOCKER COMPOSE, DOCKER MACHINE and KITEMATIC
  - Docker for Mac
    - If there are multiple account on a machine, then quit Docker on one account, to run it on another account. 
  - Docker for windows
    - windows version docker must be compatible.
    - virtualization must be enabled 
      - CPU under performance tab, virtualization enabled
    - Docker NATIVELY runs only on Windows 10 & above versions

# Docker commands.
- container and image
  - container is a running environment(STATE) on local machine for an image.
  - all the environment stuffs ( virtual file system, environment config ) are provided by the container other than the image from the repository. 
  - container has a port 5000.
  - file system is vitual in containers.
- Tag 
  - tag is basically the version of an image.  Example - lastest/ 9.6 
- docker pull 
  - pull an image LOCALLY. 
  - docker pull redis
- docker run 
  - pull an image & start the container. Optionally it will download if an image is not present on my system.
- docker images 
  - list down all images LOCALLY.
- docker ps 
  - list RUNNING containers. 
  - ps stands for PROCESS STATUS.
- docker run -d redis 
  - run a container in a DETACHED MODE. We will get the ID of the container as an output.
- docker start CONTAINER_ID 
  - start a STOPPED container. This CONTAINER_ID is taken from the docker ps command. 
- docker stop CONTAINER_ID 
  - stop the RUNNING container. This CONTAINER_ID is taken from the docker ps command.
- docker logs CONTAINER_ID 
  - print the logs of a container.
- docker logs CONTAINER_NAME 
  - print the logs of a container. CONTAINER_NAME is taken from docker ps command.
- docker ps -a 
  - List all RUNNING / NOT-RUNNING containers. 
  - NOT-RUNNING containers can be started again.
- docker run redis:4.0
- docker exec -it CONTAINER_ID
  - going inside a container.
  - open an interactive terminal (-it) of a container.
- container port vs host port
  - multiple containers can run on a single host machine.
  - each container will have a port.
  - Multiple container can have the same port.
  - HOST_PORT to CONTAINER_PORT binding must be UNIQUE on a SINGLE host machine.
  - Container will listen to the request only if HOST_PORT to CONTAINER_PORT binding is present.
  - This binding is done while running an image.
  - docker run -p6000:6379 redis 
    - Binding HOST_PORT 6000 to CONTAINER_PORT 6379.
  - docker run -p6001:6379 redis:4.0 
    - Binding HOST_PORT 6001 to CONTAINER_PORT 6379.
  - docker run -p6002:6379 --name old-redis redis:4.0  
    - old-redis is the CONTAINER_NAME
- docker run vs docker start command
  - docker run -> optionally download the image if it is not present LOCALLY.
  - both commands start the container. 
  - docker run -> start a NEW container.
  - docker start -> start a STOPPED container.
  - Docker run -> can have multiple options ( -d -p --name ) while starting running itself.
  - docker start -> will start the container with all the options which were already given in docker run command. New options cannot be given.
# Debug a container.
- docker run -d -p 60001:6379 --name redis-older redis:4.0
  - creating a container with name "redis-older"
- docker run -d -p 60001:6379 --name redis-latest redis
  - creating a container with name 'redis-latest'
- docker logs CONTAINER_ID -> Logs of a container
- docker logs CONTAINER_NAME -> Logs of a container
- docker exec -it CONTAINER_ID /bin/bash
  - inside the container as a root user.
  - virtual file system inside the container.
  - these containers are light weight linux images hence all the linux command won't be available like "curl" command.
  - ls -> list all the child folder.
  - pwd -> print out the directory.
  - cd / -> go to homme directory.
  - ls -> what is inside the home directory.
  - env -> print all the environment variables.
  - exit -> out of the terminal.

# Developing with containers.
- JS(UI) + Node JS (backend) application with "MangoDB" as database and "Mango-express" as SQL client.
- MangoDB and Mango-express are downloaded and run from the docker repository.
    - docker pull mango -> pulling lastest version of MangoDB image.
    - docker pull mango-express -> pulling lastest version of Mango-express image.
- mango-express will connect to the MangoDB through docker network concept.
  - Docker Network (Connection between mango and mango-expres)
    - docker creates isolated docker-network where containers are running in.
    - two containers in the same docker network can talk to each other with just the container name.
    - "docker network ls" command
        - docker networks by defaults.
    - "docker network create mango-network" command 
        - creates our own custom network "mango-network"
    - run mangodb in "mango-network".
        - "docker run -p 27017:27017 -d -e MANGO_INITDB_ROOT_USERNAME=admin -e MANGO_INITDB_ROOT_PASSWORD=password --name mangodb --net mango-network mango"
        
- applications which run outside of our docker network (our js application), will connect to docker network (mangodb & mango-express) using the localhost:27017
- browser(which is on the host, outside the docker network) will connect to our js application using host:port number (localhost:8080)
- our node js application will connect with the "mangodb" database.
- Once this application is built, we will push the codebase to GIT. Jenkins will build and create an image out of this.
- This image can be pushed back to docker repository. 
- This image and MangoDB need to be FECTHED from the docker repository and deployed on a DEPLOYMENT SERVER. 


# Docker compose
  - Running multiple services.
# Docker file
# Private Docker Repository ( AWS )
# Deploying containerized application.
# Volumes
  - Persisting data.
# Volumes Demo


