FROM alpine:3.6
ARG USER="Inderpal Singh"
ARG DIR="/home/inder"
RUN mkdir $DIR
WORKDIR $DIR
RUN echo "Hello $USER" > message.txt
CMD pwd;cat message.txt
