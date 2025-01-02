FROM php:8.3-apache

RUN apt-get update && apt-get upgrade -y && \
    apt-get install -y git && \
    docker-php-ext-install -j$(nproc) pdo_mysql && \
    apt-get install -y libzip-dev && apt-get install -y zip &&\
    apt-get install -y docker-php-ext-install zip && \
    apt-get clean && rm -rf /var/lib/apt/lists/*

RUN curl -sS https://getcomposer.org/installer | php -- --install-dir=/usr/local/bin --filename=composer

WORKDIR /var/www/html

RUN /usr/sbin/a2enmod rewrite

COPY default.conf /etc/apache2/sites-available/000-default.conf