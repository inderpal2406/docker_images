# This Dockerfile will build an nginx server from ubuntu base image.

FROM ubuntu:latest

# we can change this env var value and docker will build again from this instruction instead of using cache updating and installing
# updated versions of available package versions, thus refreshing the image env
ENV Refreshed_at 28-12-2019_7:32_UTC

# We don't specify multiple RUN instructions to run multiple commands, as each INSTRUCTION will result in a new image layer
# So, we follow below pattern to run multiple commands in a single RUN instruction using && \ symbols
# && will execute next command only if previous command is successful (0 as exit status) and \ denotes escape sequence for ne line
# to check default user of an image, we can check the image documentation on Dockerhub.
# no need to use sudo as by default in official ubuntu, we login as root user
# if we still want to change user for next commands, then we can do so with USER instruction

RUN apt-get update && \         
    apt-get install -y nginx && \ 
    echo "Hi, I am your container" > /var/www/html/index.html

# exposes container port
EXPOSE 80

# defining healthcheck
HEALTHCHECK --interval=10s --timeout=1m --retries=5 CMD curl http://localhost:8080 || exit 1
