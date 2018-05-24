FROM php:7.2-fpm

MAINTAINER ikeykey

COPY ./php.ini-development /usr/local/etc/php/php.ini

RUN apt-get update && apt-get install -y zip unzip curl git
RUN php -r "copy('https://getcomposer.org/installer', 'composer-setup.php');"
RUN php composer-setup.php --install-dir=/usr/bin --filename=composer
RUN php -r "unlink('composer-setup.php');"

RUN pecl install swoole
RUN echo "extension=swoole.so" >> /usr/local/etc/php/php.ini

EXPOSE 9000