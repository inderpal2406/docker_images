FROM alpine:3.6
ARG USER=inder
ARG DIR=/home/inder
RUN mkdir $DIR
WORKDIR $DIR
RUN echo "Hello $USER. I am in build process and will be hot baked into the image." > message.txt
CMD cat message.txt
