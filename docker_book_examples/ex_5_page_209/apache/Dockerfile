# install apache2 webserver to server our jekyll website from compiled code in /var/www/html

FROM ubuntu:latest

MAINTAINER Inderpal Singh <inderpal2406@gmail.com>

ENV REFRESHED_AT=11-01-2020_13:30_UTC APACHE_RUN_USER=www-data APACHE_RUN_GROUP=www-data APACHE_LOG_DIR=/var/log/apache2 

ENV APACHE_PID_FILE=/var/run/apache2.pid APACHE_RUN_DIR=/var/run/apache2 APACHE_LOCK_DIR=/var/run/apache2

RUN apt-get update -y && \
    apt-get install -y apache2 && \
    mkdir -p $APACHE_LOG_DIR $APACHE_LOCK_DIR $APACHE_RUN_DIR

VOLUME /var/www/html

WORKDIR /var/www/html

EXPOSE 80

ENTRYPOINT [ "/usr/sbin/apache2" ]

CMD [ "-D", "FOREGROUND" ]
