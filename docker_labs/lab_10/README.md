## Lab 10
This is to demonstrate the use of `RUN` instruction.

* `RUN` instruction executes specified commands on top of the below layer and creates a new layer.
* `RUN` can be wrote in below 2 forms,
  * Shell form
  * Exec form

## Commands
```
atom shell.sh
docker build -t inderpal2406/alpine-run:v0.0.1 .
docker images
docker image history inderpal2406/alpine-run:v0.0.1
docker image history inderpal2406/alpine-run:v0.0.1 | tail +2 | wc -l
docker image ls inderpal2406/alpine-run:v0.0.1
```

* The shell script was executed within the build process.
* No of layers in image built using multiple RUN instructions are 8.
* Image size of image built using multiple RUN instructions is 4.03 MB.

## Combining different RUN instructions into one.
Before doing so, here is the original Dockerfile,
```
FROM alpine:3.6
RUN mkdir /tmp/test
WORKDIR /tmp/test
COPY shell.sh .
RUN ls -l shell.sh
RUN chmod +x shell.sh
RUN ./shell.sh
```

After combining different RUN instructions into one as in current Dockerfile,
```
docker build -t inderpal2406/alpine-run:v0.0.2 .
docker image history inderpal2406/alpine-run:v0.0.2 | tail +2 | wc -l
docker image ls inderpal2406/alpine-run:v0.0.2
```

* No of layers now is 6 though the size is same as before 4.03 MB. But this may affect large size images.
