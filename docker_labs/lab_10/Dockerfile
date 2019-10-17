FROM alpine:3.6
RUN mkdir /tmp/test
WORKDIR /tmp/test
COPY shell.sh .
RUN \
  ls -l shell.sh && \
  chmod +x shell.sh && \
  ./shell.sh
