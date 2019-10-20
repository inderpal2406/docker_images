## Lab 12

## `restart` command
* The `docker-compose restart` command helps us to restart all the services mentioned in `docker-compose.yml` file.
* The `docker-compose restart <service name>` command helps us to restart specific services.
* If we restart a specific service, and confirm the container status using `docker ps` then the STATUS gets changed w.r.t. time the container is up but the CREATED time doesn't change.

More info: http://dockerlabs.collabnix.com/intermediate/workshop/DockerCompose/restart_command.html
