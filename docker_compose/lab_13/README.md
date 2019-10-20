## Lab 13

## `pause` command
* The `docker-compose pause` command helps us to pause services.
* `docker-compose pause <service name>` to pause specific service.

## Output
```
$ docker-compose ps
 Name               Command             State                     Ports                  
-----------------------------------------------------------------------------------------
Mysqldb   docker-entrypoint.sh mysqld   Paused   0.0.0.0:3306->3306/tcp, 33060/tcp       
Nginx     nginx -g daemon off;          Paused   0.0.0.0:443->443/tcp, 0.0.0.0:80->80/tcp
```

## `unpause` command
* The `docker-compose unpause` command helps us to unpause services.
* `docker-compose pause <service name>` to unpause specific service.

## Output
```
$ docker-compose ps
 Name               Command             State                    Ports                  
----------------------------------------------------------------------------------------
Mysqldb   docker-entrypoint.sh mysqld   Up      0.0.0.0:3306->3306/tcp, 33060/tcp       
Nginx     nginx -g daemon off;          Up      0.0.0.0:443->443/tcp, 0.0.0.0:80->80/tcp
```

## Output for specific services
```
$ docker-compose ps
 Name               Command             State                     Ports                  
-----------------------------------------------------------------------------------------
Mysqldb   docker-entrypoint.sh mysqld   Up       0.0.0.0:3306->3306/tcp, 33060/tcp       
Nginx     nginx -g daemon off;          Paused   0.0.0.0:443->443/tcp, 0.0.0.0:80->80/tcp
```

```
$ docker-compose ps
 Name               Command             State                    Ports                  
----------------------------------------------------------------------------------------
Mysqldb   docker-entrypoint.sh mysqld   Up      0.0.0.0:3306->3306/tcp, 33060/tcp       
Nginx     nginx -g daemon off;          Up      0.0.0.0:443->443/tcp, 0.0.0.0:80->80/tcp
```

**Curl didn't give any reply when the `webserver` service was in `paused` state** Otherwise it should have given any error. i had to press CTRL+C to come out.

More info: http://dockerlabs.collabnix.com/intermediate/workshop/DockerCompose/pause_command.html
