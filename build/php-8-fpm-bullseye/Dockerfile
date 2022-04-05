FROM php:8.0-fpm-bullseye

ENV TZ=Asia/Shanghai

RUN mv "$PHP_INI_DIR/php.ini-production" "$PHP_INI_DIR/php.ini" \
    && sed -i "s/www-data:\/var\/www:\/usr\/sbin\/nologin/www-data:\/var\/www:\/bin\/bash/g" /etc/passwd \
    && pecl install redis \
    && apt-get update \
	&& apt-get install -y libzip-dev libpng-dev libxml2-dev libargon2-dev \
    && docker-php-ext-configure opcache --enable-opcache \
	&& docker-php-ext-install -j$(nproc) pdo gettext gd zip bcmath intl pcntl shmop soap sockets sysvsem \
    && docker-php-ext-install pdo_mysql opcache \
    && docker-php-ext-enable redis \
    && php -r "readfile('https://install.phpcomposer.com/installer');" | php -- --install-dir=/usr/bin --filename=composer


