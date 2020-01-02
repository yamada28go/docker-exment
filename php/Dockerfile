FROM php:7.2-fpm

# Exmentバージョンを設定する
ENV EXMENT_VERSION 3.0.13

# install php-ext
RUN apt-get update && apt-get install -y \
  git vim unzip libxml2-dev libpng-dev \
  && docker-php-ext-install mbstring mysqli dom gd zip pdo_mysql \
  && apt-get clean

# install composer
RUN curl -sS https://getcomposer.org/installer | php -- --install-dir=/usr/local/bin --filename=composer

COPY php.ini /usr/local/etc/php/

# install exment
WORKDIR /var/www
RUN apt-get update && apt-get install -y wget

# install exment
RUN composer create-project "laravel/laravel=5.6.*" exment &&\
  cd exment &&\
  composer require exceedone/exment:${EXMENT_VERSION} &&\
  php artisan vendor:publish --provider="Exceedone\Exment\ExmentServiceProvider"

# 権限を指定する
RUN chown -R www-data:www-data exment &&\
  chmod 755 -R /var/www/exment/storage &&\
  chmod 755 -R /var/www/exment/bootstrap/cache
