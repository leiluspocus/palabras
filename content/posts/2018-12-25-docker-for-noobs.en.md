--- 
title: Docker Cheatsheet
date: "2018-08-25T19:23:42+00:00"
description: Juste un petit article mémo sur Docker
template: post
draft: false
slug: /fr/docker-memo
category: Cheatsheets
tags:
  - shell
  - docker
  - command line interface
---

Petit article mémo sur Docker

# Getting Started
make sure that client can talk to engine + current version
docker version 

An image is the application we want to run. 
A container is an instance of the image running as a process. 

# Containers 
docker container run --publish 80:80 nginx 
Left number == Host port. Make sure it's not already used (otherwise bind error)
1. Pull down "nginx" image from Docker Hub
2. Started a new container accessible from that image.
3. Opened port 80 on the host IP
4. Routes that traffic to the container IP port 80. 

Option --detach => Run in the background. 
docker container run --detach --publish 80:80 nginx


### List all running containers
docker container ls == docker ps

### Nommer un container
docker container run --detach --name LENOM --publish 13370:80 nginx

### Voir les derniers logs d'un container
docker container logs nom_container

### Voir les processus s'exécutant dans un container 
docker container top nom_container

# Ce qui se passe quand on run un container

Changing the defaults :
- The listening port on the host
- Change version of the image
- Change CMD executed when the container runs on start

A container is a process running on your host environment system. 

# Run multiple containers 
docker container run --detach --name nginx --publish 80:80 nginx 
docker container run --detach --name mysql --env MYSQL_RANDOM_ROOT_PASSWORD=yes --publish 3306:3306 mysql
docker container run --detach --name httpd --publish 8080:80 httpd

# See what's going on in containers
Process list in one container
docker container top container_name

### Details of one container config
docker container inspect container_name

### Performance stats for all containers
docker container stats container_name

# Getting a shell inside container 
docker container run -it
Start new container interactively 
T for terminal
I to keep the session open

docker container exec -it 
Run additionnal command in a running container

Alpine is smaller than Ubuntu. 

Publishing ports is always in HOST:CONTAINER format.

docker container run <stuff> nginx
use nginx:alpine instead !

# Assignment - CLI App Testing 
docker container run --rm -it --name centos centos:7 bash
curl 7.29

docker container run --rm -it --name ubuntu ubuntu:14.04 bash
curl 7.35 


docker container run --detach -it --name centos centos:7 bash

# Assignment - Round Robin 
docker network create round_robin_network

docker container run --detach --network round_robin_network --net-alias search elasticsearch:2 

docker container run --rm --net round_robin_network alpine nslookup search


docker container run --rm --net round_robin_network centos curl -s search:9200

# Container Images 
An image is made of app binaries and dependencies. Metadata about the image data and how to run the image. 
Not a complete OS. No kernel, kernel modules. Small as one file (app binary) like golang. 
Big as Ubuntu with apt, apache, PHP and more installed. 

# Docker Hub 
docker pull nginx 
docker pull nginx:1.10.11 
Always use a specific version to prevent software from updating automatically using latest tag. 
Docker Hub = The apt package system for containers 
Alpine => Smaller than counterparts OS. 

# Docker Image Layers 
docker history mysql 
View changes on the image. 
When we download an image, we start with one layer. 
In a dockerfile, we can add more stuff using apt-get or env variables : it adds a new layer everytime. 
Each layer is uniquely identified and only stored once on a host. Save storage space.

#Image Tagging and Pushing to Docker Hub. 
Images don't have name. We refer to them using repository, tag. 
Tag => Pointer to a specific image commit. 

Add tag to existing image: docker image tag SOURCE_IMAGE:TAG TARGET_IMAGE:TAG

docker image push bretfisher/nginx. 

# Dockerfile basics
&& => Make sure these commands are run for one layer. 
CMD => final command that will be run after container is launched or restarted. 

# Running Docker Builds 
At the top => things that change the least
At the bottom => things that change the most

# Extending official images 
WORKDIR => cd pour se placer dans un répertoire. 

# Assignment: Build Your Own Image with a Dockerfile
Dockerfile are part process workflow and part art. 
docker image build -t node-app . 
docker container run -p 3000:80 --rm node-app

# Container Lifetime and Persistent Data
Containers are usually immutable and ephemeral. Temporary and disposable. 
Volumes need manual deletion. 

Use friendly name for volumes to see which volumes is attached to which container. 
docker container run -d --name mysql -e MYSQL_ALLOW_EMPTY_ROOT_PASSWORD=true -v mysql-database:/var/lib/mysql mysql

If we need to specify the driver, we need to create the volume ahead of container creation. 

Partager dossier courant pour live modifs
docker container run -d --name nginx -p 80:80 -v $(pwd):/usr/share/nginx/html nginx 

## Assignment - Named Volumes 
docker container run -d --name postgres -v pgsql-data:/var/lib/postgresql/data postgres:9.6.1

docker container logs postgres

docker container stop postgres

docker container run -d --name postgres2 -v pgsql-data:/var/lib/postgresql/data postgres:9.6.2

## Assignment - Bind Mounts 
Super cool for local development. 

docker run -p 80:4000 -v $(pwd):/site bretfisher/jekyll-serve 

# Docker Compose

Configure relationships between containers
Save our docker container run settings in easy-to-read file. Create one-liner developer environment startups. 

We specify in that file the containers we need to run ... 

## docker-compose.yml 
depends_on : explique les dépendances entre containers au yaml

 docker-compose up # setup volumes networks and start all containers

 docker-compose down # stop all containers and remove containers / volumes / networks 

 docker-compose logs to see logs, -d detach to run in background.  

 docker-compose ps , top, down. 

 # Assignment - Writing a compose file 
 use the service name as the DNS name. localhost won't work. use name.
 Volumes are never removed automatically.