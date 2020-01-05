FROM ubuntu:latest

MAINTAINER Inderpal Singh <inderpal2406@gmail.com>

ENV REFRESHED_AT 05/01/2020_08:00_UTC

RUN apt-get update && \
    apt-get install -y redis-server redis-tools 

EXPOSE 6379

ENTRYPOINT [ "/usr/bin/redis-server", "--protected-mode no" ]
