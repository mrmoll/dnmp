FROM php:5.6-fpm-alpine
MAINTAINER mrmoll
RUN sed -i 's/dl-cdn.alpinelinux.org/mirrors.ustc.edu.cn/g' /etc/apk/repositories \
    && apk update \
    && apk add --no-cache libmcrypt-dev \
    && docker-php-ext-install mysqli mcrypt pdo_mysql

# 安装 Composer
RUN curl -sS https://getcomposer.org/installer | php -- --install-dir=/usr/local/bin --filename=composer
RUN composer config -g repo.packagist composer https://packagist.laravel-china.org
