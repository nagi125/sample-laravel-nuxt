FROM php:8.1-fpm-alpine

ENV TZ Asia/Tokyo
ENV COMPOSER_ALLOW_SUPERUSER 1
ENV COMPOSER_PROCESS_TIMEOUT 0
ENV COMPOSER_NO_INTERACTION 1

RUN set -eux && \
    apk add --update-cache --no-cache openssl git autoconf g++ nodejs npm yarn oniguruma-dev postgresql-dev libtool make libzip-dev libpng-dev libjpeg-turbo-dev freetype-dev libwebp-dev libxpm-dev && \
    pecl install redis && \
    docker-php-ext-configure gd --with-freetype --with-jpeg --with-webp --with-xpm && \
    docker-php-ext-configure opcache --enable-opcache && \
    docker-php-ext-install gd pdo_pgsql pgsql opcache bcmath gd exif zip && \
    docker-php-ext-enable redis && \
    apk del autoconf g++ libtool make && \
    rm -rf /tmp/*

COPY conf/php.ini /usr/local/etc/php/php.ini
COPY conf/docker.conf /usr/local/etc/php-fpm.d/docker.conf

# Composerの準備
COPY --from=composer/composer /usr/bin/composer /usr/bin/composer

WORKDIR /app
