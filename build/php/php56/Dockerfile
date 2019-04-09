FROM php:5.6-fpm-alpine
RUN apt-get update \
    && apt-get install iputils-ping \
    && docker-php-ext-install mysqli && docker-php-ext-enable mysqli