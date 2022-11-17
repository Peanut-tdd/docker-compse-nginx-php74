FROM php:7.4-fpm
RUN docker-php-ext-install pdo_mysql \
&& docker-php-ext-install bcmath \
&& curl -L -o /tmp/redis.tar.gz https://github.com/phpredis/phpredis/archive/5.3.6.tar.gz \
&& tar xfz /tmp/redis.tar.gz \
&& rm -r /tmp/redis.tar.gz \
&& mkdir -p /usr/src/php/ext \
&& mv phpredis-5.3.6 /usr/src/php/ext/redis \
&& docker-php-ext-install redis \
&& curl -L -o  /tmp/protobuf.tgz  https://pecl.php.net/get/protobuf-3.21.9.tgz \
&& tar xfz /tmp/protobuf.tgz \
&& rm -r /tmp/protobuf.tgz \
&& mkdir -p /usr/src/php/ext \
&& mv protobuf-3.21.9 /usr/src/php/ext/protobuf \
&& docker-php-ext-install protobuf
