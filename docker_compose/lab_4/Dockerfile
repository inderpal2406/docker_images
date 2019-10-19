FROM nginx:alpine
LABEL MAINTAINER="inderpal2406" NAME="nginx"
ENV REFRESHED_AT 19/10/2019-12:02
RUN echo "Welcome to custom Nginx webserver!" > /usr/share/nginx/html/index.html
EXPOSE 80
EXPOSE 443
ENTRYPOINT [ "nginx" ]
CMD [ "-g", "daemon off;" ]
