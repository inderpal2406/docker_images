## Lab 1
To practise writing Dockerfile.<br>
In this lab, we'll prepare a docker image with git installed in it.<br>
This image will be built using Dockerfile.<br>

## Commands
```
docker build -t="inderpal2406/alpine-git:v0.0.1" .
docker run --name alpine-git -dit inderpal2406/alpine-git:v0.0.1
docker ps
docker attach xxxx
git --version
```

In above commands, `xxxx` is the 4 digits of the container_id.
