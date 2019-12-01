FROM php:7.2-fpm

# Exmentバージョンを設定する
ENV EXMENT_VERSION 3.0.7

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

RUN wget https://exment.net/downloads/ja/exment.zip&&\
  unzip exment.zip &&\
  rm exment.zip 

RUN chown -R www-data:www-data exment &&\
  chmod 755 -R /var/www/exment/storage &&\
  chmod 755 -R /var/www/exment/bootstrap/cache

# 本来は、以下でバージョン固定して実現できるハズ
#RUN wget https://github.com/exceedone/exment/archive/v${EXMENT_VERSION}.tar.gz&&\
#  tar xvfz v${EXMENT_VERSION}.tar.gz  &&\
#  mv exment-${EXMENT_VERSION}/ exment && \
#  rm v${EXMENT_VERSION}.tar.gz

#RUN git clone https://github.com/exceedone/exment.git\
#  cd exment &&\
#  git checkout master && \
#  git checkout v${EXMENT_VERSION} && 

