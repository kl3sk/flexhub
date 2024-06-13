FROM php:8.2-fpm-alpine

COPY --from=composer:latest /usr/bin/composer /usr/local/bin/composer

RUN apk add zip libzip-dev libpq-dev icu-dev $PHPIZE_DEPS &&  \
    docker-php-ext-install zip pdo pdo_pgsql intl && \
    pecl install redis && docker-php-ext-enable redis

WORKDIR /application

ADD ./backend /application

ENV COMPOSER_ALLOW_SUPERUSER=1
#RUN composer install

EXPOSE 9000

#CMD ["php-fpm"]
