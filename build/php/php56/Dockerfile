FROM php:5.6-fpm-alpine
MAINTAINER mrmoll
RUN usermod -u 1000 www-data
RUN sed -i 's/dl-cdn.alpinelinux.org/mirrors.ustc.edu.cn/g' /etc/apk/repositories \
    && apk update \
    && apk add --no-cache libmcrypt-dev \
    && docker-php-ext-install mysqli mcrypt pdo_mysql
