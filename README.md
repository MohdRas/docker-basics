# docker-basics

BASICS
- What is Container & docker
  - Own isolated environment ( application + dependencies + configuration)
      - No need to install any application directly on OS.
      - One commmand to fetch the container & start it.
      - Different versions of the same application can be installed & used.
      - docker run posgresql
  - To package an application in a container with all its dependencies & configuration.
  - With Containers, development & operations team work together to package application in a container.
  - Portable actifact(JAR/WAR + Database service + Instructions ). Development to Operations team. Operations team deploy the application.
      - Dependency versions conflicts.
      - Misunderstanding between development & operations team.
      - Textual guide for deployment about External Dependencies & configurations.
  - Development & deployment of an application is more efficient now.
  - Development improvement - No need to follow different instructions to install applications ( DB ) for each OS & Application.
  - Deployment imporovement - No need to share steps to deploy it along with its artifact, dependencies and configuration.
  - Where to store these containers? 
      - container repository is used for this.
  - Private repository of containers. 
      - Companies have their own private repository for their own containers.
  - Public Repository ( DockerHub ) for Docker Containers 
      - Only docker containers can reside.
      - Official & non-official container images ( Jenkins ) .
   
  - Layers of a container
    - base image layer - basic OS & dependencies
    - dependency layer - library + framework
    - code layer - code + configuration
    - build layer - tools & scripts to compile the application
    - run layer - runtime dependencies + configuration

- Docker vs VM.
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
