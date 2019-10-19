## Lab 1

## `version` command.

The `docker-compose --version` or `docker-compose version` command helps us check the version of the `docker-compose` binary. This binary is in `usr/local/bin` directory.

```
$ docker-compose --version
docker-compose version 1.24.1, build 4667896b
```

```
$ docker-compose version
docker-compose version 1.24.1, build 4667896b
docker-py version: 3.7.3
CPython version: 3.6.8
OpenSSL version: OpenSSL 1.1.0j  20 Nov 2018
```

docker-py is the Docker Remote API, it does everything the docker command does, but from within Python – run containers, manage them, pull/push images, etc.
