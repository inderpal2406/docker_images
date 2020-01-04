FROM ubuntu:latest

MAINTAINER Inderpal Singh <inderpal2406@gmail.com>

ENV REFRESHED_AT 04-01-2020_20:00_UTC

ADD test.tar .

RUN apt-get update && \
    apt-get install -y nginx && \
    mkdir -p /var/www/html/website/ && \
    mv /global.conf /etc/nginx/conf.d/ && \
    mv /nginx.conf /etc/nginx/

EXPOSE 80
