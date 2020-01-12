FROM ubuntu:latest

MAINTAINER Inderpal Singh <inderpal2406@gmail.com>

ENV REFRESHED_AT=12-01-2020_11:30_UTC

RUN apt-get update -y && \
    apt-get install -y nodejs npm 

COPY ./ /opt/nodeapp/

WORKDIR /opt/nodeapp

RUN npm install

VOLUME /var/log/nodeapp

EXPOSE 3000

ENTRYPOINT [ "nodejs", "server.js" ]
