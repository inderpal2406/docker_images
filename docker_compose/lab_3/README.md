## Lab 3

## `config` command
The `docker-compose config` command lets us validate our `docker-compose.yml` file. <br>
**NOTE:** `docker-compose config` command has to be executed in same directory as the `docker-compose.yml` file.

## Exercise
1. Create `docker-compose.yml` file.
2. Validate it using `docker-compose config` command.
3. Edit `docker-compose.yml` file and make some errors.
4. Validate again.

## Commands
```
vi docker-compose.yml
docker-compose config
```

## Output with no errors
```
$ docker-compose config
services:
  webserver:
    container_name: webserver
    image: nginx:alpine
    ports:
    - 80:80/tcp
    - 443:443/tcp
    restart: unless-stopped
version: '3.1'
```

## Output with errors
Changed `services` key to `service`

```
$ docker-compose config
ERROR: The Compose file './docker-compose.yml' is invalid because:
Invalid top-level property "service". Valid top-level sections for this Compose file are: version, services, networks, volumes, secrets, and extensions starting with "x-".

You might be seeing this error because you're using the wrong Compose file version. Either specify a supported version (e.g "2.2" or "3.3") and place your service definitions under the `services` key, or omit the `version` key and place your service definitions at the root of the file to use version 1.
For more on the Compose file format versions, see https://docs.docker.com/compose/compose-file/
```

So, valis top-level sections for `docker-compose.yml` file are,
- version
- services
- networks
- volumes
- secrets
- extensions starting with "x-"
