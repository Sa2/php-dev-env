FROM php:7.1-fpm

ENV EXECUTE_USER developer
RUN apt-get update && apt-get install -y libmcrypt-dev mysql-client zip unzip vim
RUN docker-php-ext-install mcrypt 
RUN curl -sS https://getcomposer.org/installer | php && \
    mv composer.phar /usr/local/bin/composer && \
    # user追加
    useradd -m -s /bin/bash -u 1000 ${EXECUTE_USER} && \
    # www.conf修正
    sed -i "s/user\ \=\ www-data/user\ \=\ ${EXECUTE_USER}/g" /usr/local/etc/php-fpm.d/www.conf && \
    sed -i "s/group\ \=\ www-data/group\ \=\ ${EXECUTE_USER}/g" /usr/local/etc/php-fpm.d/www.conf
WORKDIR /var/www/app