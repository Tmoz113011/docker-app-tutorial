FROM php:7.2-fpm

RUN apt-get update && apt-get install -y libmcrypt-dev \
    libmagickwand-dev --no-install-recommends \
    git \
    vim \
    && pecl install imagick redis xdebug \
    && docker-php-ext-enable imagick \
    redis \
    && docker-php-ext-install pdo_mysql mbstring

RUN curl -sS https://getcomposer.org/installer | php \
    && mv composer.phar /usr/local/bin/composer \
    && chmod +x /usr/local/bin/composer \
    && curl -sL https://deb.nodesource.com/setup_12.x | bash - \
    && apt-get install -y nodejs

COPY . /var/www/html

VOLUME /var/www/html
RUN composer install \
    && npm install

EXPOSE 9000
