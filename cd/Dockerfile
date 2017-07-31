FROM php:5.6-apache
MAINTAINER "endou_cai@gmail.com"
ENV container docker

# 引入源
RUN mv /etc/apt/sources.list /etc/apt/sources.list.bak
COPY ./xcd/cd/sources.list /etc/apt/

# 更新源
RUN apt-get update

RUN apt-get -y install ImageMagick unzip
RUN apt-get -y install ffmpeg

#安装mcrypt
RUN apt-get -y install libmcrypt-dev
RUN docker-php-ext-install mcrypt

# 安装mysqli, pdo_mysql, redis, xdebug
RUN docker-php-ext-install mysqli \
    && docker-php-ext-install pdo_mysql \
        && pecl install redis \
        && echo "extension=redis.so" > $PHP_INI_DIR/conf.d/redis.ini \
        && pecl install xdebug

# 启动header，为了跨域
RUN a2enmod headers

# 跨域+警告级别
COPY ./xcd/cd/000-default.conf /etc/apache2/sites-enabled/

# 开启错误日志
COPY ./xcd/cd/php.ini /usr/local/etc/php/php.ini

COPY ./ /var/www/html/
