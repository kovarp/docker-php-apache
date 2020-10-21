FROM php:5.3-apache

RUN a2enmod rewrite

# msmtp configuration
COPY .docker/php-apache/msmtprc /etc/msmtprc

COPY .docker/php-apache/php.ini /usr/local/etc/php/