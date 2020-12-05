ARG PHP_VERSION=""
FROM php:${PHP_VERSION:+${PHP_VERSION}-}fpm-alpine
RUN apk update; \
    apk upgrade;
    
RUN apk add --no-cache $PHPIZE_DEPS icu-dev openssl-dev icu-libs\
    && docker-php-ext-install pdo pdo_mysql intl\ 
    && pecl install xdebug \
    && docker-php-ext-enable xdebug opcache

RUN cp /usr/local/etc/php/php.ini-development /usr/local/etc/php/php.ini

RUN sed -i 's/upload_max_filesize = 2M/upload_max_filesize = 100M/g' /usr/local/etc/php/php.ini

RUN sed -i 's/post_max_size = 8M/post_max_size = 100M/g' /usr/local/etc/php/php.ini

RUN apk add --update nodejs npm

RUN chown -R www-data:82 /var/www
