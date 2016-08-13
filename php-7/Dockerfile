FROM php:7
RUN apt-get update && apt-get install -y curl sudo git libxslt-dev mercurial zlib1g-dev
RUN docker-php-ext-install soap
RUN docker-php-ext-install zip
RUN docker-php-ext-install xsl
RUN docker-php-ext-install mbstring
RUN docker-php-ext-install gettext
RUN pecl install xdebug
RUN docker-php-ext-enable xdebug
RUN curl -sS https://getcomposer.org/installer | php -- --install-dir=/usr/local/bin --filename=composer
