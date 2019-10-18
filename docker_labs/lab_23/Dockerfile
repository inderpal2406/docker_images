FROM alpine:latest
LABEL NAME="hello-inderpal"
ARG DIR="/mydir"
RUN mkdir $DIR
WORKDIR $DIR
COPY hello_inderpal.sh .
RUN chmod +x hello_inderpal.sh
ENTRYPOINT [ "./hello_inderpal.sh" ]
