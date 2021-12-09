FROM php:8.0-fpm as base

RUN apt-get update && apt-get install -y --no-install-recommends gnupg \
    netcat \
    sudo \
    libicu-dev \
    libfreetype6-dev \
    libjpeg-dev \
    libpng-dev \
    libxml2-dev \
    libsodium-dev \
    libxslt-dev \
    libzip-dev \
    rsync \
    unzip \
    nano \
    vim \
    less \
    git \
    cron \
    ;

RUN pecl install xdebug

RUN docker-php-ext-configure gd --with-freetype=/usr/include/ --with-jpeg=/usr/include/
RUN docker-php-ext-install bcmath \
    intl \
    gd \
    opcache \
    soap \
    sodium \
    xsl \
    pdo_mysql \
    zip \
    sockets \
    ;

COPY --from=composer:latest /usr/bin/composer /usr/bin/composer
ENV COMPOSER_HOME=/tmp/composer

CMD ["php-fpm"]
