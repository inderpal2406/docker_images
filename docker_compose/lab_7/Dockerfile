# Version v0.0.2
FROM nginx:alpine
LABEl MAINTAINER="inderpal2406" NAME="nginx-alpine"
ENV REFRESHED_AT 20/10/2019-11:12
RUN echo "Hello from Nginx!" > /usr/share/nginx/html/index.html
EXPOSE 80/tcp
EXPOSE 443/tcp
CMD [ "-g", "daemon off;" ]
ENTRYPOINT [ "nginx" ]
