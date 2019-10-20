## Lab 6

## `push` command.
* The `docker-compose push` command help you tou push the service images to Docker Hub or your own private Docker registry.

## Exercise
* Dockerfile for custom docker image
* Create a docker-compose.yml file
* Build the image using docker-compose
* Upload the image to Docker registry

## Commands
```
vi Dockerfile_nginx
vi Dockerfile_httpd
vi docker-compose.yml
docker-compose config
docker-compose build
docker-compose push
```

This pushed both images to DockerHub.

However, to push a specific image only using `docker-compose`, the command is `docker-compose push <service name>`

To test this, I added additional service named `git` in `docker-compose.yml` file and ran `docker-compose build` and `docker-compose push git`, and the single image was pushed to DockerHub.

Running, `docker-compose build` again, resulted into build of nginx and httpd images as well, but they were built quickly from cache, and their image ids, time of creation didn't change in `docker images` output.
