## Lab 15

## `port` command
The `docker-compose port` command prints the public/network facing port for a service.

## Syntax
`docker-compose port <service name> <port number>` <br>
This will check that which localhost port is mapped to specified port number of specified service name in the command.

## Output
```
$ docker-compose port webserver 80
0.0.0.0:80
```
* This shows that the localhost's port 80 (0.0.0.0:80) is mapped to `webserver` service container's port 80.
* **Localhost is denoted by `127.0.0.0`, then why `0.0.0.0` is being used?**
* **If we have more than one containers constituting `webserver` service, then will all of the containers' port 80 be mapped to single port 80 of localhost?**
* These port mappings using `docker-compose port` command won't be listed if containers are not running!




* Port mapping in Docker world are always specified in format of `host:container`.
