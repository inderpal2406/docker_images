FROM alpine:latest
LABEL NAME="python-hello-app"
ARG DIR="/mydir"
RUN \
  apk update && \
  apk add python && \
  mkdir $DIR
WORKDIR $DIR
COPY hello.py .
CMD [ "/mydir/hello.py"]
ENTRYPOINT [ "python" ]
