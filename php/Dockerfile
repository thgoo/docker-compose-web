FROM php:7-fpm
MAINTAINER "Thiago Augusto" <thiagoeu@gmail.com>
# install necessary extensions
RUN apt-get update && apt-get install -y libfreetype6-dev libjpeg62-turbo-dev libmcrypt-dev libpng12-dev libssl-dev libmagickwand-dev --no-install-recommends \
    && docker-php-ext-configure \
        gd --with-freetype-dir=/usr/include/ --with-jpeg-dir=/usr/include/ \
    && docker-php-ext-install -j$(nproc) iconv mcrypt pdo_mysql gd \
    && pecl install mongodb imagick \
    && docker-php-ext-enable mongodb imagick

# edit php.ini
RUN echo 'date.timezone=America/Sao_Paulo' >> /usr/local/etc/php/php.ini && \
    echo 'upload_max_filesize=256M' >> /usr/local/etc/php/php.ini && \
    echo 'post_max_size=256M' >> /usr/local/etc/php/php.ini && \
    echo 'display_errors=On' >> /usr/local/etc/php/php.ini && \
    echo 'display_startup_errors=On' >> /usr/local/etc/php/php.ini