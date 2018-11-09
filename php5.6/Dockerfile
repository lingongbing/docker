FROM php:5.6-fpm

LABEL maintainer="lingongbign"

ENV DEBIAN_FRONTEND=noninteractive

RUN apt-get update && apt-get install -y \
        libfreetype6-dev \
        libjpeg62-turbo-dev \
        libpng-dev \
    && docker-php-ext-install -j$(nproc) iconv \
    && docker-php-ext-configure gd --with-freetype-dir=/usr/include/ --with-jpeg-dir=/usr/include/ \
    && docker-php-ext-install -j$(nproc) gd \
    && docker-php-ext-install pdo_mysql \
    && pecl install redis \
    && pecl install xdebug-2.5.5 \
    && docker-php-ext-enable redis xdebug

RUN apt-get update && apt-get install unzip \
    && curl -L -o /tmp/cphalcon.zip https://github.com/phalcon/cphalcon/archive/master.zip \
    && unzip -d /tmp/ /tmp/cphalcon.zip \
    && cd /tmp/cphalcon-master/build \
    && ./install \
    && apt-get remove unzip -y \
    && rm -rf /var/lib/apt/lists/* \
    && rm -rf /tmp/cphalcon* \
    && docker-php-ext-enable phalcon