FROM php:7.4-apache

RUN docker-php-ext-install pdo_mysql \
&& docker-php-ext-install mysqli \
&& a2enmod rewrite

COPY .docker/php-apache/php.ini /usr/local/etc/php/

RUN apt-get update -y && apt-get install -y -qq git \
	libwebp-dev\
	libpng-dev\
	zlib1g-dev \
	libjpeg62-turbo-dev \
	apt-transport-https \
	libfreetype6-dev \
	libmcrypt-dev \
	libssl-dev \
	libzip-dev \
	zip unzip \
	wget \
	msmtp \
	vim

RUN docker-php-ext-configure gd --with-freetype --with-jpeg --with-webp
RUN docker-php-ext-install -j$(nproc) iconv zip gd bcmath

# msmtp configuration
COPY .docker/php-apache/msmtprc /etc/msmtprc

RUN curl -sS https://getcomposer.org/installer | php -- --install-dir=/usr/local/bin --filename=composer