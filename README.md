#  docker-basics

BASICS
# What is Container & docker
  - container has its own isolated environment ( application + dependencies + configuration)
    - With containers, no need to install any application directly on OS.
    - One commmand to fetch the image & start it.
    - Different versions of the image can be downloaded and run.
    - docker run postgres:9.6 -->> download + run an image->> postgres:9.6=name of the image:version
    - find first image locally ->> then download it from docker hub.
    - each layer of the image is downloaded separately.
    - Downloading two versions of the same image - >> If we download second version then the layers which were aleady downloaded as per of first version, won't be downloaded again.
    - docker ps - All running containers on my local machine.
  - docker image vs docker container
    - docker image is the one which actually reside on repository ( docker hub)
    - docker image is the portable/movable arftifact.
    - docker image is pulled and started on my local machine ->> it is now "a container running on my local machine". ->> it creates a container environment.
  - To package an application in a container with all its dependencies & configuration.
  - With Containers, development & operations team work together to package an application in a container.
  - Deployment before containers - 
    - Portable actifact(JAR/WAR + Database service + Instructions ). Development team give it to Operations team. Operations team deploy the application.
    - Dependency versions conflicts.
    - Misunderstanding between development & operations team.
    - Textual guide for deployment about External Dependencies & configurations.
  - Development & deployment of an application is more efficient now.
  - Development improvement - No need to follow different instructions to install applications ( DB ) for each OS & Application.
  - Deployment imporovement - No need to share steps to deploy it along with its artifact, dependencies and configuration.
  - Where to store these images? 
    - image repository is used for this.
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
  - What part of OS they virtualize ?
  - Docker virtualize the Applications layer and uses the Kernel of the Host machine.
  - Size -->> Docker image smaller than VM
  - Speed ->> Docker containers start & run faster than VM
  - Compatibility -->> VM of any OS can run on Host OS.
  - VM virtualizes the applications layer and OS Kernel layer. Virtualizes the complete OS.
  - Hardware + OS + Software Applications - 
    - Applications layer-  run on Kernel Layer
    - OS Kernel layer - communicate with Hardware ( CPU + MEMORY )
    - Hardware laqyer
    - OS Layer (OS Kernel + Applications )
    - Run Linux based image might not be compatible on windows machine ( Windows Kernel + Windows Applications ) for windows version < 10 and old mac versions.
    - This can be achieved through WSL2 ( Windows subsystem for Linux), Linex based Kernel inside VM of Windows.
    - This means Linux image container is not directly running on windows kernel rather on the linux kernel inside windows VM.
    - Host kernel can natively support docker images or not ( Windows kernel can not run Linux based image natively)
    - Docker ToolBox(Legacy Solution) is used to run any OS based image on any Host OS.
# Docker installation.
- Installation will differ for each OS and its version.
- Install docker on Windows/Mac/Linux
- Community Edition ( CE ) & Enterprise Edition ( EE ) 
- Prerequisites ( System Requirements )
  - OS version & Hardware criteria (RAM)
  - Installation includes - Docker Engine, Docker CLI, Docker Compose, Docker Machine and Kitematic
  - Docker for Mac
    - If there are multiple account on a machine then quit Docker on one account to run it on another account. 
  - Docker for windows
    - windows version must be compatible.
    - virtualization must be enabled ( CPU under performance tab, virtualization enabled )
    - Docker natively runs only on Windows 10.

# Docker commands.
- container and image
  - container is a running environment of an image.
  - all the environment stuffs ( file system, environment config ) are provided by the container other than the image from the repository. 
  - container has a port 5000.
  - file system is vitual in containers.
- Tag - tag is basically the version of an image.  Example - lastest/ 9.6 
- docker pull - pull an image locally. 
  - docker pull redis
- docker run - pull an image & start the container. Optionally it will download if an image is not present on my system.
- docker images - list existing images irrespective of their status ( running/downoaded )
- docker ps - list RUNNING containers.
- docker run -d redis - run a container in a DETACHED MODE. We will get the ID of the container as an output.
- docker start container_id - start a STOPPED container. This container_id is taken from the docker ps command. 
- docker stop container_id - stop the RUNNING container. This container_id is taken from the docker ps command.
- docker ps -a - List all RUNNING / NOT-RUNNING containers. NOT-RUNNING containers can be started again.
- docker run redis:4.0
- docker exec -it
- docker logs
- container port vs host port
  - multiple containers can run on a single host machine.
  - host port - port of the host machine. Host ports can be multiple but must be unique.
  - container port - port of a container. Multiple container can have same port.
  - All containers can have same port but the corresponding host ports must be unique.
  - host port : container port - mapping must be unique. ( 8080:5000, 8089:5000, 8081:5000)
  - Container will listen to the request if binding of host port to container port is done while running a container.
  - docker run -p6000:6379 redis - Binding host port 6000 to container port 6379.
  - docker run -p6001:6379 redis:4.0 - Binding host port 6001 to container port 6379.

# Debug a container.
# Developing with containers.
# Docker compose
  - Running multiple services.
# Docker file
# Private Docker Repository ( AWS )
# Deploying containerized application.
# Volumes
  - Persisting data.
# Volumes Demo


