## Lab 5

## `pull` command
The `docker-compose pull` command pull down the images which is specified under each service of docker-compose file from the docker hub.

## Exercise
1. Write docker-compose.yml file.
2. Pull images of each service.
3. Pull image of a single service.

## Commands
```
vi docker-compose.yml
docker-compose config
docker-compose pull
docker images
docker rmi $(docker images -q)
docker-compose pull webserver
```

* To pull image for a specified service, we can execute `docker-compose pull <service 1 name> <service 2 name>`.
* By default images will be pulled from DockerHub unless we specify FQDN of other image registry alone with image name and tag in `image` specification of docker-compose.yml file.
