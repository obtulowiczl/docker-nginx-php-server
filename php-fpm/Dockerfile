FROM php:8.1-fpm-alpine
RUN apk add nano
RUN apk add bash
RUN apk add curl
RUN docker-php-ext-install sockets pdo_mysql pdo 
# && docker-php-ext-install pdo_mysql \
# && docker-php-ext-install sockets
RUN set -x \
	&& addgroup -g 101 -S nginx \
	&& adduser -u 101 -D -S -G nginx nginx
COPY ./php-fpm/zz-docker.conf /usr/local/etc/php-fpm.d/zz-docker.conf
#RUN curl -sS https://getcomposer.org/installer | php -- --install-dir=/usr/local/bin --filename=composer
COPY --from=composer:latest /usr/bin/composer /usr/bin/composer
