FROM php:5.6

RUN apt-get update \
  && apt-get install -y libcurl4-openssl-dev sudo git libxslt-dev mercurial subversion zlib1g-dev graphviz zip libmcrypt-dev libicu-dev g++ nodejs npm libpng-dev libgd-dev \
  && apt-get clean \
  && docker-php-ext-install soap \
  && docker-php-ext-install zip \
  && docker-php-ext-install xsl \
  && docker-php-ext-configure gd --with-freetype-dir=/usr/include/ --with-jpeg-dir=/usr/include/ \
  && docker-php-ext-install gd \
  && docker-php-ext-install mcrypt \
  && docker-php-ext-install mbstring \
  && docker-php-ext-install gettext \
  && docker-php-ext-install curl \
  && docker-php-ext-install mysqli \
  && docker-php-ext-install pdo_mysql \
  && docker-php-ext-install json \
  && docker-php-ext-install intl \
  && docker-php-ext-install opcache

RUN curl -sS https://getcomposer.org/installer | php -- --install-dir=/usr/local/bin --filename=composer
RUN ln -s /usr/bin/nodejs /usr/bin/node
RUN npm install -g bower grunt-cli
RUN echo '{ "allow_root": true, "storage": {"packages": ".bower-cache/"} }' > ~/.bowerrc
RUN echo 'cache=.node-cache' > ~/.npmrc
RUN echo '{ "config": { "cache-dir": ".composer-cache" } }' > ~/.composer/composer.json
RUN composer global require --no-progress --no-interaction --no-suggest deployer/deployer deployer/recipes hirak/prestissimo
RUN ln -s ~/.composer/vendor/bin/dep /usr/bin/deployer
RUN curl -O https://raw.githubusercontent.com/vishnubob/wait-for-it/master/wait-for-it.sh && chmod +x wait-for-it.sh && ln -s ~/wait-for-it.sh /usr/bin/wait-for-it

