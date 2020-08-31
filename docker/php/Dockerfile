FROM php:7.3-fpm

RUN echo "Launch php"

RUN rm /etc/apt/preferences.d/no-debian-php \
    && apt-get update && apt-get install -y \
    libfreetype6-dev \
    libjpeg62-turbo-dev \
    libpng-dev \
    libmcrypt-dev \
    libmagickwand-dev \
    libxml2-dev \
    zlib1g-dev \
    imagemagick \
    libzip-dev \
    unzip \
    git \
    msmtp \
    zlib1g-dev \
    libicu-dev \
    g++ \
    && docker-php-ext-install -j$(nproc) iconv \
    && docker-php-ext-configure gd --with-freetype-dir=/usr/include/ --with-jpeg-dir=/usr/include/ \
    && docker-php-ext-install -j$(nproc) gd \
    && docker-php-ext-install -j$(nproc) pdo_mysql \
    && docker-php-ext-install -j$(nproc) soap \
    && docker-php-ext-install -j$(nproc) zip \
    && docker-php-ext-configure intl

RUN php -r "copy('https://getcomposer.org/installer', 'composer-setup.php');" \
    && php composer-setup.php --install-dir=/usr/bin/ --filename=composer \
    && php -r "unlink('composer-setup.php');"

WORKDIR /var/www/symfony

COPY ./php.ini /usr/local/etc/php/

RUN usermod -u 1000 www-data
