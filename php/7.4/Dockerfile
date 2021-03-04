FROM php:7.4-fpm
RUN apt-get update && apt-get install -y \
    libfreetype6-dev \
    libjpeg62-turbo-dev \
    libpng-dev \
    libicu-dev \
    libxml2-dev \
    libxslt-dev \
    libzip-dev \
    git vim unzip cron \
    --no-install-recommends \
    && rm -r /var/lib/apt/lists/*

RUN docker-php-ext-configure gd --with-freetype \
    --with-jpeg \
    && docker-php-ext-install -j$(nproc) gd

RUN docker-php-ext-configure intl \
    && docker-php-ext-install -j$(nproc) intl

RUN docker-php-ext-install -j$(nproc) opcache bcmath pdo_mysql soap xsl zip sockets

# install xdebug
RUN set -xe && \
        docker-php-source extract && \
        pecl install -f xdebug-2.9.8 && \
        docker-php-ext-enable xdebug && \
        docker-php-source delete && \
        php -v && \
        php -m

# Create user magento
RUN useradd -m -s /bin/bash magento \
    && usermod -a -G www-data magento

RUN cp "$PHP_INI_DIR/php.ini-development" "$PHP_INI_DIR/php.ini"

ADD ./php.ini /usr/local/etc/php/php.ini

ADD ./composer/1.10.20/composer.phar /usr/local/bin/composer

CMD ["php-fpm"]

EXPOSE 9000