FROM php:7.2-fpm

# Exmentバージョンを設定する
ENV EXMENT_VERSION 3.0.7

RUN apt-get update && apt-get install -y \
  git vim unzip libxml2-dev libpng-dev \
  && docker-php-ext-install mbstring mysqli dom gd zip pdo_mysql \
  && apt-get clean
# install composer
RUN curl -sS https://getcomposer.org/installer | php -- --install-dir=/usr/local/bin --filename=composer


# install composer
#RUN php -r "copy('https://getcomposer.org/installer', 'composer-setup.php');" &&\
#  php composer-setup.php &&\
#  php -r "unlink('composer-setup.php');" &&\
#  mv composer.phar /usr/local/bin/composer

COPY php.ini /usr/local/etc/php/

# install exment
WORKDIR /var/www
RUN apt-get update && apt-get install -y wget

RUN wget https://exment.net/downloads/ja/exment.zip&&\
  unzip exment.zip &&\
  rm exment.zip 

#RUN chmod 777 -R /var/www/exment/storage &&\
#  chmod 777 -R /var/www/exment/bootstrap/cache

RUN chmod 777 -R /var/www/exment


#RUN wget https://github.com/exceedone/exment/archive/v${EXMENT_VERSION}.tar.gz&&\
#  tar xvfz v${EXMENT_VERSION}.tar.gz  &&\
#  mv exment-${EXMENT_VERSION}/ exment && \
#  rm v${EXMENT_VERSION}.tar.gz

#RUN git clone https://github.com/exceedone/exment.git\
#  cd exment &&\
#  git checkout master && \
#  git checkout v${EXMENT_VERSION} && 




