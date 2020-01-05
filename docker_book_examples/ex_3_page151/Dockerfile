FROM ubuntu:latest

MAINTAINER Inderpal Singh <inderpal2406@gmail.com>

ENV REFRESHED_AT 05-01-2020_07:00_UTC

RUN apt-get update && \
    apt-get install -y ruby ruby-dev build-essential redis-tools && \
    gem install --no-rdoc --no-ri sinatra json redis && \
    mkdir -p /opt/webapp

EXPOSE 4567

CMD [ "/opt/webapp/bin/webapp" ]
