## Lab 16
To demonstrate `EXPOSE` instruction.

* The `EXPOSE` instruction expose a port, the protocol can be UDP or TCP associated with the indicated port, default is TCP with no specification.
* Regardless of the `EXPOSE` settings, `EXPOSE` port can be override using `-p` flag while starting the container.
* `EXPOSE` only lets us expose container ports, but not map host ports to container ports. The mapping of ports can be done when we run container from image with the help of `-p` option.

## Commands
```
docker build -t inderpal2406/nginx-alpine-expose:v0.0.1 .
docker run --rm --name expose -d inderpal2406/nginx-alpine-expose:v0.0.1
docker ps
```

The `docker ps` command lets us know which host port is mapped to which container port or which ports have been exposed.
