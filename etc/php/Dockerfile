FROM php:7.1-fpm

RUN apt-get update > /dev/null && apt-get install -y \
    git \
    unzip \
    libfreetype6-dev \
    libjpeg62-turbo-dev \
    libmcrypt-dev \
    libpng12-dev \
    zlib1g-dev \
    libicu-dev \
    jpegoptim \
    g++ \
    libxrender1 \
    libfontconfig \
    vim mc htop > /dev/null \
    && docker-php-ext-install -j$(nproc) iconv mcrypt > /dev/null \
    && docker-php-ext-install intl > /dev/null \
    && docker-php-ext-install zip > /dev/null


# Install Composer
RUN curl -sS https://getcomposer.org/installer | php \
        && mv composer.phar /usr/local/bin/ \
        && ln -s /usr/local/bin/composer.phar /usr/local/bin/composer

# Install MySQL PDO
RUN docker-php-ext-install pdo pdo_mysql > /dev/null

# Install GD library
RUN docker-php-ext-install gd > /dev/null

# Install XDebug extention
RUN pecl install xdebug > /dev/null && docker-php-ext-enable xdebug > /dev/null


WORKDIR /var/www/html
