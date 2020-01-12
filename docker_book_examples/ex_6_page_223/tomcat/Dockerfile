# image with TOMCAT installed and same docker volume as fetcher image

FROM ubuntu:latest

MAINTAINER Inderpal Singh <inderpal2406@gmail.com>

ENV REFRESHED_AT=12-01-2020_05:00_UTC CATALINA_HOME=/usr/share/tomcat8 CATALINA_BASE=/var/lib/tomcat8

ENV CATALINA_PID=/var/run/tomcat8.pid CATALINA_SH=/usr/share/tomcat8/bin/catalina.sh CATALINA_TMPDIR=/tmp/tomcat8-tomcat8-tmp

RUN apt-get update -y && \
    apt-get install -y tomcat8 default-jdk && \
    mkdir $CATALINA_TMPDIR

VOLUME /var/lib/tomcat8/webapps

EXPOSE 8080

ENTRYPOINT [ "/usr/share/tomcat8/bin/catalina.sh", "run" ]
