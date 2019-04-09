FROM php:5.6-fpm-alpine
MAINTAINER mrmoll
RUN sed -i 's/dl-cdn.alpinelinux.org/mirrors.ustc.edu.cn/g' /etc/apk/repositories \
    docker-php-ext-install mysqli && docker-php-ext-enable mysqli