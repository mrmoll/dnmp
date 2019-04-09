FROM php:5.6-fpm-alpine
MAINTAINER mrmoll
RUN sed -i 's/dl-cdn.alpinelinux.org/mirrors.ustc.edu.cn/g' /etc/apk/repositories \
    && apk update \
    && docker-php-ext-enable mysqli
    && docker-php-ext-enable pdo_mysql