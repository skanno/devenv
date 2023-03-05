FROM php:8.1-fpm

COPY php.ini /usr/local/etc/php/

RUN apt update
RUN apt install -y \
git \
libicu-dev \
libonig-dev \
libpq-dev \
libzip-dev \
mariadb-client \
unzip \
vim \
wget \
zlib1g-dev

# Install PHP Extensions
RUN docker-php-ext-install \
intl \
pdo_mysql \
zip

ENV COMPOSER_ALLOW_SUPERUSER 1
ENV COMPOSER_NO_INTERACTION 1
COPY --from=composer/composer /usr/bin/composer /usr/bin/composer

# Install Composer
RUN composer self-update

WORKDIR /var/www

RUN chown -R www-data:www-data /var/www
