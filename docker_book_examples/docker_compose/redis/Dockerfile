FROM ubuntu:latest

MAINTAINER Inderpal Singh <inderpal2406@gmail.com>

ENV REFRESHED_AT 13-01-2020_10:30_UTC

RUN apt-get update -y && \
    apt-get install -y redis-server redis-tools

EXPOSE 6379

CMD [ "redis-server", "--protected-mode no" ]
