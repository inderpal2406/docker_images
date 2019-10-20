## Lab 7

## `up` command
The `docker-compose up` command helps us to bring up a multi-container application, which we have described in our `docker-compose.yml` file.

## Exercise
* Create a docker-compose.yml with custom image
* Build container and network
* Bring up the containers

## Commands
```
vi Dockerfile
vi docker-compose.yml
docker-compose config
docker-compose up --no-start    # This will build image, create containers, networks, volumes as described in docker-compose.yml but won't run/start containers
docker-compose ps               # to check container status, it shows our Nginx and Mysqldb containers as created.
docker ps                       # to check container status, basicaly it doesn't show any container running at the moment
docker-compose up -d            # to run containers in background as daemons
docker-compose ps
docker ps
curl localhost:80 OR curl http://localhost  # to check webserver response
docker exec -it Mysqldb mysql -u root -p    # to check login into Mysql DB.
docker-compose up -d --build    # to rebuild image and bring the stack up
```

* `docker images` list images w.r.t thier creation/build time. The most recently built images are displayed at the top.
* `docker ps` and `docker ps -a` list containers w.r.t thier creation time. The most recently created containers are displayed at the top. Please note that containers are not sorted w.r.t. their status i.e. `Exited (0) 2 days/4 seconds/2 hours ago` or so.
* `docker-compose down` not only stops containers but also removes them.
* We can use `docker-compose up --build` command instead of `docker-compose up`, because the latter will also build the image if needed, but the prior looks more complete whether executed first time or subsequently.
