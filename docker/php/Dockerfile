FROM php:8.2-fpm

ARG UID
EXPOSE $UID

RUN adduser -u ${UID} --disabled-password --gecos "" inventario
RUN mkdir /home/inventario/.ssh
RUN chown -R inventario:inventario /home/inventario/
RUN echo "StrictHostKeyChecking no" >> /home/inventario/.ssh/config
RUN echo "export COLUMNS=300" >> /home/inventario/.bashrc
RUN echo "alias sf=/appdata/www/bin/console" >> /home/inventario/.bashrc

COPY php.ini /usr/local/etc/php/php.ini

RUN apt-get update \
    && apt-get install -y git acl openssl openssh-client wget zip vim librabbitmq-dev libssh-dev \
    && apt-get install -y libpng-dev zlib1g-dev libzip-dev libxml2-dev libicu-dev libpq-dev\
    && docker-php-ext-install intl pdo pdo_pgsql zip gd soap bcmath sockets \
    && pecl install amqp xdebug \
    && docker-php-ext-enable --ini-name 05-opcache.ini opcache amqp xdebug
COPY xdebug.ini /usr/local/etc/php/conf.d/xdebug.ini

RUN curl --insecure https://getcomposer.org/composer.phar -o /usr/bin/composer && chmod +x /usr/bin/composer
RUN composer self-update

#RUN wget https://cs.symfony.com/download/php-cs-fixer-v2.phar -O php-cs-fixer
#RUN chmod a+x php-cs-fixer
#RUN mv php-cs-fixer /usr/local/bin/php-cs-fixer

RUN mkdir -p /app/inventario

WORKDIR /app/inventario