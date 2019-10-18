## Lab 13
To check if `ENV` takes value with spaces in it.

## Dockerfile
```
FROM alpine:3.6
ENV MSG Hello Inder
CMD echo $MSG
```

## Commands
```
docker build -t inderpal2406/alpine-env-check:v0.0.1 .
docker run inderpal2406/alpine-env-check:v0.0.1
```

## Output from container
```
Hello Inder
```

* So, `ENV` accepts value with spaces.
* Even `ENV MSG "Hello Inder, you're good."` worked and gave an output of `Hello Inder, you're good.`

## Override `ARG` during build time.
This was done using Dockerfile of lab_12.

` docker build --build-arg USER="Inderpal Singh Saini" -t inderpal2406/alpine-build-arg:v0.1 .` worked.
`docker build --build-arg USER=Inderpal Singh Saini -t inderpal2406/alpine-build-arg:v0.2 .` didn't work as build command considered Singh and Saini as different build arguments to be processed.
