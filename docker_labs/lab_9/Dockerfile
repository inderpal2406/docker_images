FROM alpine:3.6

ENV GO_TO /home/inder
ENV FOLDER_1 test1
ENV FOLDER_2 test2

RUN mkdir /home/inder

WORKDIR $GO_TO

RUN mkdir test1

WORKDIR $FOLDER_1

RUN mkdir test2

WORKDIR $FOLDER_2

ENTRYPOINT pwd
