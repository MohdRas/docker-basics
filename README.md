# docker-basics

BASICS
- What is Container & docker
  - base image layer - basic OS & dependencies
  - dependency layer - library + framework
  - code layer - code + configuration
  - build layer - tools & scripts to compile the application
  - run layer - runtime dependencies + configuration
  - To package an application with all its dependencies & configuration.
  - Portable actifact. It can move between development & operation team.
  - Development & deployment of an application is more efficient now.
  - Development improvement - No need to follow different steps for each OS & Application.
  - Deployment imporovement - No need to share steps to deploy it along with its artifact, dependencies and configuration
  - Where to store these containers? 
      - container repository is used for this.
  - Private repository of containers. 
      - Companies have their own private repository for their own containers.
  - Public Repository ( DockerHub ) for Docker Containers 
      - Only docker containers can reside.

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
