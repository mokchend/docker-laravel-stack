FROM php:7.4-fpm

MAINTAINER Chenda Mok <chenda.mok@gmail.com>

# debconf: delaying package configuration, since apt-utils is not installed
RUN apt-get update -y && apt-get install -y \
        libjpeg62-turbo-dev \
        libmcrypt-dev \
        libpng-dev \
        libicu-dev \
        libpq-dev \
        libxpm-dev \
        libvpx-dev \
        # No package 'libzip' found
        libssl-dev \
        libzip-dev \
    && pecl install mcrypt-1.0.3 \
    && docker-php-ext-enable mcrypt \
    && pecl install xdebug \
    && docker-php-ext-enable xdebug \
    # && docker-php-ext-install -j$(nproc) mcrypt \
    && docker-php-ext-install -j$(nproc) intl \
    && docker-php-ext-install -j$(nproc) zip \
    && docker-php-ext-install -j$(nproc) pgsql \
    && docker-php-ext-install -j$(nproc) pdo_pgsql \
    && docker-php-ext-install -j$(nproc) exif
    # https://github.com/docker-library/php/issues/931
    # configure: error: unrecognized options: --with-png
    # && docker-php-ext-configure gd \
    #     --with-png=/usr/include/ \
    #     --with-jpeg=/usr/include/ \
    #     --with-freetype=/usr/include/


