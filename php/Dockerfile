
FROM php:7.4-apache

RUN apt-get update && apt-get install -y \
    libfreetype6-dev \
    libjpeg62-turbo-dev \
    libvpx-dev \
    zlib1g-dev \
    libzip-dev \
    nodejs \
    yarn

RUN docker-php-ext-install pdo pdo_mysql mysqli zip opcache
RUN pecl install xdebug-2.9.6 \
    && docker-php-ext-enable xdebug \
    && docker-php-ext-configure gd \
    && docker-php-ext-install gd

RUN curl -sS https://getcomposer.org/installer | php -- --install-dir=/usr/local/bin --filename=composer && \
    ln -s $(composer config --global home) /root/composer
ENV PATH=$PATH:/root/composer/vendor/bin COMPOSER_ALLOW_SUPERUSER=1

RUN a2enmod rewrite
