# docker-basics

BASICS
- What is Container & docker
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

- Docker vs VM.
  - Both are virtualization tools.
  - What part of OS they virtualize ?
  - Docker virtualize the Applications layer and uses the Kernel of the Host machine.
  - Size -->> Docker image smaller than VM
  - Speed ->> Docker containers run faster than VM
  - Compatibility -->> VM of any OS can run on Host OS.
  - VM virtualizes the applications layer and OS Kernel layer. Virtualizes the complete OS.
  - Hardware + OS + Software Applications - 
    - Applications layer-  run on Kernel Layer
    - OS Kernel layer - communicate with Hardware ( CPU + MEMORY )
    - Hardware laqyer
    - OS Layer (OS Kernel + Applications )
- Docker installation.
- Docker commands.
- Debug a container.
- Developing with containers.
- Docker compose
  - Running multiple services.
- Docker file
- Private Docker Repository ( AWS )
- Deploying containerized application.
- Volumes
  - Persisting data.
- Volumes Demo


CONTAINER

- To package our application with its dependencies & configuration.
- Portable actifact between development & operation team.
- To improve development/deployment of an application.
- Development improvement - No need to follow different steps for each OS & Application.
- Deployment imporovement - No need to share steps to deploy it with artifacts, dependencies, configuration
- base image layer - basic OS & dependencies
- dependency layer - library + framework
- code layer - code + configuration
- build layer - tools & scripts to compile the application
- run layer - runtime dependencies + configuration


DEMO
 - Developing with container.
 - Docker compose - running multiple services.
 - Docker file - to build docker image
 - Private Docker Repository (AWS)  - push docker image
 - Deploy containerized application.
 - Volumes - Persist data in docker
