## Lab 11
To demonstrate difference between `ENV` and `ARG` instruction.

* We can comment out lines in Dockerfile using `#`.
* If we're copying any file into image from local system, though we don't change the instructions in Dockerfile but change the file to be copied, Docker detects it and doesn't build from cache from that instruction onwards.
* Value of a variable set using `ENV` can be used in subsequent instructions in Dockerfile, no matter if it's `RUN` instruction or `WORKIR` instruction. The variable set using `ENV` is also available inside the container started from the same image.

Below Dockerfile was executed to test above points,
```
FROM alpine:3.6
ENV DIRECTORY /home/inder
RUN mkdir $DIRECTORY
WORKDIR $DIRECTORY
RUN echo "This is directory name as $DIRECTORY."
# ENTRYPOINT ["pwd"] # This showed the directory as /home/inder whenever a container was spinned from the image. The container used to stop after displaying pwd output.
CMD sh
```

To test `ARG` functionality, we have below Dockerfile,
```
FROM alpine:3.6
ARG USER=inder
ARG DIR=/home/inder
RUN mkdir $DIR
WORKDIR $DIR
RUN echo "Hello $USER. I am in build process and will be hot baked into the image." > message.txt
CMD cat message.txt
```

* When we built the image and started a container from it, it displayed the message `Hello inder. I am in build process and will be hot baked into the image.`
* But the variables $USER and $DIR were not available inside env of container. This was verified by changing the `CMD` to `sh` and running an interactive container.
