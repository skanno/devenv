FROM php:8.1-fpm

COPY php.ini /usr/local/etc/php/

RUN apt update
RUN apt install -y gcc
RUN apt install -y git
RUN apt install -y unzip
RUN apt install -y vim
RUN apt install -y wget

RUN apt install -y libicu-dev # Used in intl.
RUN apt install -y libonig-dev # Used in mbstring.
RUN apt install -y libssl-dev # Used in ftp.
RUN apt install -y libzip-dev # Used in zip.

# Install PHP Extensions
RUN docker-php-ext-install calendar
RUN docker-php-ext-install ctype
RUN docker-php-ext-install exif
RUN docker-php-ext-install fileinfo
RUN docker-php-ext-install ftp
RUN docker-php-ext-install gettext
RUN docker-php-ext-install iconv
RUN docker-php-ext-install intl
RUN docker-php-ext-install mbstring
RUN docker-php-ext-install pdo
RUN docker-php-ext-install pdo_mysql
RUN docker-php-ext-install posix
RUN docker-php-ext-install sockets
RUN docker-php-ext-install zip

# Install Composer
ENV COMPOSER_ALLOW_SUPERUSER 1
ENV COMPOSER_NO_INTERACTION 1
COPY --from=composer/composer /usr/bin/composer /usr/bin/composer
RUN composer self-update

COPY php.ini /usr/local/etc/php/

WORKDIR /var/www

RUN chown -R www-data:www-data /var/www
