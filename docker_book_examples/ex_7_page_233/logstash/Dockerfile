FROM ubuntu:latest

MAINTAINER Inderpal Singh <inderpal2406@gmail.com>

ENV REFRESHED_AT=12-01-2020_18:00_UTC

RUN apt-get update -y && \
    apt-get install -y wget apt-transport-https && \
    wget -O - https://artifacts.elastic.co/GPG-KEY-elasticsearch | apt-key add - && \
    echo "deb https://artifacts.elastic.co/packages/7.x/apt stable main" | tee -a /etc/apt/sources.list.d/elastic-7.x.list && \
    apt-get update -y && \
    apt-get install -y logstash default-jdk

COPY logstash.conf /etc/

WORKDIR /opt/logstash

ENTRYPOINT [ "/bin/logstash" ]

CMD [ "--config=/etc/logstash.conf" ]
