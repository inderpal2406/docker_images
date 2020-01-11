# To install jekyll framework and dependencies required to compile code.

FROM ubuntu:latest

MAINTAINER Inderpal Singh <inderpal2406@gmail.com>

ENV REFRESHED_AT 11-01-2020_13:30_UTC

RUN apt-get update && \
    apt-get install -y ruby ruby-dev build-essential nodejs && \
    gem install jekyll -v 2.5.3

VOLUME [ "/data", "/var/www/html" ]

WORKDIR /data

ENTRYPOINT [ "jekyll", "build", "--destination=/var/www/html" ]
