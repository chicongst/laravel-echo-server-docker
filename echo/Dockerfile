# Docker image for laravel echo server
FROM ubuntu:18.04

# Create app directory
RUN mkdir -p /usr/src/app

WORKDIR /usr/src/app

# Install nginx

RUN apt-get update \
    && apt-get install -y software-properties-common \
    && apt-add-repository -y ppa:nginx/stable \
    && apt-get update \
    && apt-get install -y nginx \
    && rm -rf /var/lib/apt/lists/*

RUN ln -sf /dev/stdout /var/log/nginx/access.log \
    && ln -sf /dev/stderr /var/log/nginx/error.log

ADD nginx.conf /etc/nginx/sites-available/default

#Install Node

RUN apt-get update \
    && apt-get -y install curl gnupg \
    && curl -sL https://deb.nodesource.com/setup_10.x  | bash - \
    && apt-get -y install nodejs

# Install pm2

RUN npm install pm2 -g


EXPOSE 80 6001

CMD ["nginx", "-g", "daemon off;"]
