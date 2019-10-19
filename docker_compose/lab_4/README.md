## Lab 4

## `build` command
`docker-compose build` command is specifically used to build an image. The path to build context and Dockerfile can be specified in `docker-compose.yml` file.

## Exercise
1. Write a custom Nginx Dockerfile.
2. Write `docker-compose.yml` file.
3. Specify build context and Dockerfile in it.
4. Verify `docker-compose.yml` file.
5. Build image using `docker-compose build`.

## Commands
```
vi Dockerfile
vi docker-compose.yml
docker-compose config
docker-compose build
docker images
docker run inderpal2406/nginx-alpine:v0.0.1
curl localhost:80
curl localhost:443
```

OR

```
vi Dockerfile
vi docker-compose.yml
docker-compose config
docker-compose build
docker images
docker-compose up
curl localhost:80
curl localhost:443
```

* By default docker-compose will spin up one container for each service defined in `docker-compose.yml` file if we don't mention no. of containers under that service.
* In our case curl to localhost:80 worked but to localhost:443 didn't work, though the image build and `docker-compose up` didn't give any error. May be nginx cannot serve same content on 2 ports simultaneously. Need to be verified.
* if we don't execute `docker-compose build` and directly execute `docker-compose up`, docker compose will first build the image and tag it and then spin up containers from it.
* We don't get prompt back if we execute `docker-compose up`. Opened another terminal and executed curl on it. Will execute `docker-compose down` from new terminal to stop containers and get back prompt in first terminal.
* Docker compose named the container automatically based on directory of `docker-compose.yml` file and name of service in `docker-compose.yml` file. The name of container was `lab_4_web_1` where lab_4 is name of directory and web is name of service.
* In `docker-compose.yml` file, we specified below specifications,
```
build:
  context: .
  dockerfile: Dockerfile
image: inderpal2406/nginx-alpine:v0.0.1
```
* We can specify different build context as well as Dockerfile using above configuration and either specifying absolute or relative paths.
* Docker compose named our image as `inderpal2406/nginx-alpine:v0.0.1` as defined by us in `docker-compose.yml` file. If we don't do it then docker compose will name it as
* If we bring down containers (i.e. stop containers) using `docker-compose down` the containers exit with exit status as `0`. If we bring them back up using `docker-compose up` they are started again using the same name. So, executing `docker-compose up` after `docker-compose down` without executing `docker-compose rm` command will start the same stopped containers as they were not removed from the host.
* We can even press `CTRL+C` to stop containers spinned up from '`docker-compose up` command to get back our prompt, in this case docker will first try to gracefully stop containers. If they don't get stopped in 10 secs the docker will forcefully kill them.
* If we already have an image image:v1 and build another image with same name and tag then the older image is untagged and is displayed in `docker images` output with `<none>` parameters in REPOSITORY and TAG but continues to have an IMAGE ID, CREATED and SIZE parameters.
* We changed Dockerfile, but didn't change image name and tag in `docker-compose.yml` file, and executed `docker-compose up`, no new build happened and containers were brought up using the same old image. This is the expected behaviour as docker compose will just look into `docker-compose.yml` file and since it found the image mentioned in the file to be present locally, it went forward and started containers from the image.
* So, I did `docker-compose build` to build again the image and the image was built with new changes in `Dockerfile` but tagged with same repo name and tag and the old image was untagged.
* However if I change `Dockerfile` and also change name and tag of image in `docker-compose.yml` and execute `docker-compose up`, docker compose will build new repo:tag image and start containers from it. In this case, build will occur without cache from the instrction which was changed in Dockerfile. If nothing was changed in Dockerfile but only repo:tag was changed in `docker-compose.yml` file, then the new tag image would have been built from same cache from old image. This build can be triggered either using `docker-compose build` or `docker-compose up` commands. We can mention options to not use build cache from previous builds.
* However, we can use `docker-compose up --build` option if we change only `Dockerfile` and not `docker-compose.yml` file. In this case build will re-occur.
* Added `container_name` specification and executed `docker-compose up` and new container was started with name `web`.
* If we build multiple images with different tags from same `Dockerfile`, then all such images will have different names in terms of repo/name:tags but all of them will have `same image IDs`.
* I removed image mentioned in `docker-compose.yml` file and executed `docker-compose up` it rebuilt the image with repo/name:tag mentioned in `docker-compose.yml` file and started containers from it. This happened because we have build context and Dockerfile mentioned in `docker-compose.yml` file.
* Then I commented out the build commands from yml file and only specified the image in yml file and tried to bring up services, then docker compose didn't look for the specified image in local host and try to download it from remote registry. Since, I hadn't pushed this image to Dockerhub, it failed with an error of "Manifest not found, unknown manifest". However, if we use `docker-compose up --build` in this case, it'll build it from Dockerfile in current directory and build context as `.` which are the default values for Dockerfile and build context (even though build specifications are commented out in yml file).
* Other registried have to be referred to with their complete FQDN name, but Dockerhub doesn't require FQDN as it is the default registry. This is in reference to when we perform `docker login` command.
* Suppose we have logged in to 2 registries and want to pull 2 images (one from Other registry and other from Dockerhub), then I think to pull from Dockerhub, we just need to specify `docker pull repo/name:tag` and to pull from other registry, we need to specify `docker pull FQDN/repo:tag`.
* I commented the image name from yml file and executed `docker-compose up` and it built image with name `lab_4_web:latest` and ran container named `web` from it. So, the naming depends on directory name of yml file and service name.
* Then I stopped containers by pressing `CTRL+C` and again executed `docker-compose up` it didn't build image and spinned containers from the lab_4_web:latest image.
* So, docker compose don't build images again once they are built. This can be overriden with `docker-compose up --build` or `docker-compose build`.
* Docker compose will always need either `build context` or `image` to be specified in yml file. If both are not specified then it it invalid and gives below error,
```
ERROR: The Compose file is invalid because:
Service web has neither an image nor a build context specified. At least one must be provided.
```

Passing arguments to `docker-compose build` command using `arg` is left out to be read. <br>
Link: http://dockerlabs.collabnix.com/intermediate/workshop/DockerCompose/Lab_%231:Build_Command.html
