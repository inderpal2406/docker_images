## Lab 9

## `ps` command
The `docker-compose ps` command lists out the containers with details like status, Port mapping etc. It is to be noted that it'll list only the containers which constitute services defined in `docker-compose.yml` file. It won't list other running containers on the host.

Most of the `docker-compose` commands will work in the directory in which `docker-compose.yml` file is present. However, commands like `docker-compose version` will work anywhere on the host.

`docker-compose ps --services` will onnly list the services name by reading the `docker-compose.yml` file. It doesn't matter whether the services are up or not, but `docker-compose ps --services` will list the services name.
