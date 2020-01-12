# image to download WAR files
# we install wget in an ubuntu image to download war files
# we store those WAR files in a docker volume /var/lib/tomcat7/webapps

FROM ubuntu:latest

MAINTAINER Inderpal Singh <inderpal2406@gmail.com>

ENV REFRESHED_AT=12-01-2020_04:30_UTC

RUN apt-get update -y && \
    apt-get install -y wget

VOLUME /var/lib/tomcat8/webapps

WORKDIR /var/lib/tomcat8/webapps

ENTRYPOINT [ "wget" ]

CMD [ "-?" ]
