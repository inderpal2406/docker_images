#### Table of Content
* [Docker Compose](#Docker-Compose)
  * [Introduction to `docker compose`](##Introduction-to-`docker-compose`)
  * [An example of `docker-compose.yml` file](##An-example-of-`docker-compose.yml`-file)
  * [CLI Cheatsheet](##CLI-Cheatsheet)
    * [Build](###Build)
    * [Bundle](###Bundle)
    * [Config](###Config)
    * [Up](###Up)
    * [Down](###Down)
    * [Scale](###Scale)
    * [Start](###Start)
    * [Stop](###Stop)
    * [`docker-compose` cheatsheet](###`docker-compose`-cheatsheet)
  * [Difference between `Dockerfile` and `docker-compose.yml` files](##Difference-between-`Dockerfile`-and-`docker-compose.yml`-files)
  * [How to install Docker Compose?](##How-to-install-Docker-Compose?)

<a name="Docker-Compose"></a>
# Docker Compose
* These labs are being practised from Docker Workshop for intermediate users on collabnix.com.
* Here is the [online link](http://dockerlabs.collabnix.com/intermediate/workshop/)
* These labs are mainly focused on `docker compose`.

<a name="Introduction-to-`docker-compose`"></a>
## Introduction to `docker compose`
* Docker compose is a tool built by docker to ease the task to `creating and configring multiple containers`.
* Docker compose is mainly used in development environments or we can say at small scale.
* To create, configure and manage multiple containers at large scale in production environments, Docker Inc. provides a tool similar to `Docker Compose`. The tool is `Docker Swarm`.
*  Docker compose takes as input a `YAML configuration file` and creates the resources (containers, networks, volumes etc.) by communicating with the docker daemon through docker api.
* Compose project is the `official open source project` for Docker and is responsible for the `rapid orchestration` of Docker container clusters.
* The code is currently open sourced at https://github.com/docker/compose
* Through the introduction in the first part, we know that using a `Dockerfile` template file allows users to easily define a separate application container.
* However, in daily work, it is often the case that multiple containers need to cooperate to complete a certain task.
* For example, to implement a Web project, in addition to the Web service container itself, it is often necessary to add a back-end database service container, and even a load balancing container.
* `Compose` just meets this need. It allows the user to define a `set of associated application containers` as a project through a separate `docker-compose.yml` template file (YAML format).
* There are two important concepts in Compose :
  * `Service`: Several container instances running the same image are termed as one service.
  * `Project`: A complete business unit consisting of a set of associated application containers, defined in the docker-compose.yml file.

<a name="An-example-of-`docker-compose.yml`-file"></a>
## An example of `docker-compose.yml` file
```
version: '3'

services:
  web:
    build: .
    image: web-client
    depends_on:
      - server
    ports:
      - "8080:8080"
  server:
    image: akshitgrover/helloworld
    volumes:
      - "/app"          # Anonymous volume
      - "data:/data"    # Named volume
      - "mydata:/data"  # External volume

volumes:
  data:
  mydata:
    external: true
```

[Official link](https://docs.docker.com/compose/compose-file/) to learn `docker-compose.yml` configuration.

## CLI Cheatsheet

### Build
* Used to build services specified in docker-compose.yml file with `build` specification.
* More info can be found on [official link](https://docs.docker.com/compose/compose-file/).
* **Note:** Images build will be tagged as {DIR}_{SERVICE} unless image name is specified in the service specification.

```
docker-compose build [OPTIONS] [SERVICE...]

OPTIONS:

--compress | Command line flag to compress the build context, Build context is nothing but a directory where docker-compose.yml file is located. As this directory can container a lot of files, sending build context to the container can take a lot of time thus compression is needed.

--force-rm | Remove any intermediate container while building.

--no-cache | Build images without using any cached layers from previoud builds.

--pull | Allways pull newer version of the base image.

-m, --memory | Set memory limit for the container used for building the image.

--parallel | Exploit go routines to parallely build images, As docker daemon is written in go.

--build-arg key=val | Pass any varaible to the dockerfile from the command line.


SERVICE:

If you want to build any particular services instead of every service specified in the compose file pass the name (same as in the compose file) as arguments to the command.

Example:

docker-compose build --compress     # Will compress the build context of service web.
```

### Bundle
* Used to generate distributed application bundle (DAB) from the compose file.
* More info can be found on [official link](https://docs.docker.com/compose/compose-file/).

```
docker-compose bundle [OPTIONS]

OPTIONS:

--push-image | Push images to the register if any service has build specifcation.

-o, --output PATH | Output path for .dab file.
```

### Config
* Used to validate the compose file.
* **NOTE:** Run this command in direcotry where docker-compose.yml file is located.

`docker-compose config`

### Up
* Creates and starts the resources as per the specification the docker-compose.yml file.

```
docker-compose up [OPTIONS] [SERVICE...]

OPTIONS:

-d, --detach | Run containers in background.

--build | Always build images even if it exists.

--no-deps | Avoid creating any linked services.

--force-recreate | Force recreating containers even if specification is not changed.

--no-recreate | Do not recreate containers.

--no-build | Do not build any image even if it is missing.

--no-start | Just create the containers without starting them.

--scale SERVICE=NUM | Create multiple containers for a service.

-V, --renew-anon-volumes | Recreate anonymous volumes instead of getting data from previous ones.

Example:

docker-compose up -d        # Will run service containers in background
docker-compose up web       # Will start service web and server because of 'depends_on' field
docker-compose up server    # will start server service only.
```

### Down
* `Stop and clear` any resources created while lifting docker-compose.
* By default only containers and networks defined in the compose file are removed. Networks and Volumes with `external = true` and never removed.

```
docker-compose down [OPTIONS]

--rmi type | Remove images Type = all (Remove every image in the compose file), local (Remove images with no custom tag)

-v, --volumes | Remove named volumes except the external ones and also remove anonymous volumes

-t, --timeout TIMEOUT | Speficy shutdown time in seconds. (default = 10)

Example:

docker-compose down         # Will delete all containers of both web and server and no volume will be removed

docker-compose down -v      # Will also delete anonymous and data volumes.
```

### Scale
* Scale particular services.

```
docker-compose scale [SERVICE=NUM...]

Example:

docker-compose scale server=3 web=2
```

### Start
* Start created containers.

```
docker-compose start [SERVICE...]

Example:

docker-compose start        # Start containers for every service.
docker-compose start web    # Start containers only for service web.
```

### Stop
* Stop running containers.

```
docker-compose stop [SERVICE...]

Example:

docker-compose stop         # Stop containers for every service.
docker-compose stop web     # Stop containers only for service web.
```


### `docker-compose` cheatsheet
[Cheatsheet](https://github.com/collabnix/dockerlabs/blob/master/intermediate/docker-compose/compose-cheatsheet.md)

## Difference between `Dockerfile` and `docker-compose.yml` files
* A `Dockerfile` is a text document that contains all the commands/Instructions a user could call to build an image.
* For example,
```
FROM centos:latest
LABEL MAINTAINER="Inderpal Singh" NAME="CentOS-Apache"
RUN \
  yum update -y && \
  yum install -y httpd net-tools && \
  mkdir /run/httpd
EXPOSE 80
ENTRYPOINT [ "apachectl", "-D FOREGROUND" ]
```
* Using `docker build` command we can build docker image from above `Dockerfile` example.
* `Docker compose` is a tool used to create, configure, manage single/multiple containers from images built using `Dockerfile`.
* `Docker compose` can also be used to build images, but it'll also search for `Dockerfile` to build the image.
* So, we can say that it is the `Dockerfile` which defines our image while it is the `docker-compose.yml` file which defines environment of our containers.
* With `Docker compose` tool, with the help of a sigle command, we can create, configure and manage all of our services using `docker-compose.yml` configuration file.
* By default, docker-compose expects the name of the Compose file as `docker-compose.yml` or `docker-compose.yaml`. If the compose file has different name, we can specify it with `-f` flag.
* Example of a `docker-compose.yml` file.
```
version: '3'

services:
  web:
    build: .
    image: inderpal2406/web:v0.0.5
    ports:
      - "5000:5000"
    volumes:
      - .:/code
      - logvolume01:/var/log
    links:
      - redis
  redis:
    image: redis
    volumes:
      - logvolume01: {}
```

## How to install Docker Compose on Linux?
It is a three step procedure,
1. Download `docker-compose` binary from GitHub. <br>
```
sudo curl -L https://github.com/docker/compose/releases/download/1.24.1/docker-compose-`uname -s`-`uname -m` -o /usr/local/bin/docker-compose
```
2. Give executable permission to the downloaded binary. <br>
`sudo chmod +x /usr/local/bin/docker-compose`
3. Test the installation. <br>
`docker-compose --version`
