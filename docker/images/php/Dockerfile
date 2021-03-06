FROM php:7.0-fpm-alpine3.7
WORKDIR '/app'
RUN apk update && apk upgrade\
    && apk add --no-cache curl libbz2 php7-bz2 php7-pdo php7-pgsql php7-bcmath php7-zmq php7-curl bash php7-pear php7-imagick openssh\
    php7-intl \
    php7-mysqli \
    g++ \
    icu-dev \
    php7-soap \
    php7-ldap \
    php7-gd \
    php7-zip \
    php7-xmlrpc \
    php7-xml \
    php7-pspell \
    libtool \
    postgresql-dev \
    libpng-dev \
    imagemagick-c++ \
    imagemagick-dev \
    libmcrypt-dev \
    libxml2-dev \
    yaml-dev \
    bzip2 \
    aspell-dev \
    autoconf \
    build-base \
    linux-headers \
    libaio-dev \
    zlib-dev \
    git \
    subversion \
    freetype-dev \
    libjpeg-turbo-dev \
    libmcrypt-dev \
    bzip2-dev \
    libstdc++ \
    libxslt-dev \
    openldap-dev \
    hiredis-dev \
    make \
    unzip \
    ffmpeg \
    wget
RUN curl -sS https://getcomposer.org/installer | php -- --install-dir=/usr/local/bin --filename=composer
RUN docker-php-ext-configure intl
RUN docker-php-ext-install intl
RUN docker-php-ext-install gd bcmath zip bz2 pdo pdo_pgsql simplexml opcache sockets mbstring pcntl xsl pspell pgsql xmlrpc soap
RUN docker-php-ext-configure gd --with-freetype-dir=/usr/include/ --with-jpeg-dir=/usr/include/
RUN pecl install imagick
RUN docker-php-ext-enable imagick
RUN pecl install xdebug
RUN wget http://xdebug.org/files/xdebug-2.6.1.tgz
RUN tar -xvzf xdebug-2.6.1.tgz
RUN cd xdebug-2.6.1 \
    && phpize \
    && ./configure --enable-xdebug \
    && make \
    && make install \
    && cp modules/xdebug.so /usr/local/lib/php/extensions/no-debug-non-zts-20170718 \
    && echo 'zend_extension = /usr/local/lib/php/extensions/no-debug-non-zts-20170718/xdebug.so' >> /usr/local/etc/php/php.ini \
    && echo 'zend_extension = /usr/local/lib/php/extensions/no-debug-non-zts-20170718/xdebug.so' >> /etc/php7/php.ini \
    && echo 'xdebug.remote_enable=true' >> /etc/php7/php.ini \
    && echo 'xdebug.remote_host=127.0.0.1' >> /etc/php7/php.ini \
    && echo 'xdebug.remote_port=9000' >> /etc/php7/php.ini \
    && echo 'xdebug.remote_handler=dbgp' >> /etc/php7/php.ini \
    && echo 'xdebug.max_nesting_level=512' >> /etc/php7/php.ini \
    && echo 'extension=php_pgsql.so' >> /etc/php7/php.ini \
    && echo 'extension=pgsql.so' >> /etc/php7/php.ini
EXPOSE 22