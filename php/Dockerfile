FROM php:7.3-fpm

# install php-ext
RUN apt-get update && apt-get install -y \
  git vim unzip libxml2-dev libpng-dev default-mysql-client \
  && docker-php-ext-install mbstring mysqli dom gd zip pdo_mysql \
  && apt-get clean

# install composer
RUN curl -sS https://getcomposer.org/installer | php -- --install-dir=/usr/local/bin --filename=composer

COPY php.ini /usr/local/etc/php/

# install exment
WORKDIR /var/www
RUN apt-get update && apt-get install -y wget

RUN wget https://exment.net/downloads/ja/exment.zip&&\
  unzip exment.zip &&\
  rm exment.zip 

RUN chown -R www-data:www-data exment &&\
  chmod 755 -R /var/www/exment/storage &&\
  chmod 755 -R /var/www/exment/bootstrap/cache
