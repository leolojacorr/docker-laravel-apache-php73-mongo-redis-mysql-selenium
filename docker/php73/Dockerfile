# imagem base oficial
FROM php:7.3-apache

# instalacao extensoes php
RUN apt-get update \
    && apt-get install -y --no-install-recommends openssl libssl-dev libcurl4-openssl-dev mc nano \
    && pecl install mongodb \
    && cp /usr/local/etc/php/php.ini-production /usr/local/etc/php/php.ini \
    && echo "extension=mongodb.so" >> /usr/local/etc/php/php.ini \
    && echo "extension=pdo_mysql.so" >> /usr/local/etc/php/php.ini \
    && apt-get clean \
    && rm -rf /var/lib/apt/lists/*

# para o mysql no php > 5.3
RUN  \
    docker-php-ext-configure pdo_mysql --with-pdo-mysql=mysqlnd \
    && docker-php-ext-configure mysqli --with-mysqli=mysqlnd \
    && docker-php-ext-install pdo_mysql mysqli

# diretorio no servidor web da docker
WORKDIR /var/www/
    
# https://pecl.php.net/package-changelog.php?package=mongodb
#RUN docker-php-ext-enable redis mongodb

# 
# RUN echo "memory_limit=1G" >> /usr/local/etc/php.ini
# RUN echo "post_max_size=100M" >> /usr/local/etc/php.ini
# RUN echo "upload_max_filesize=100M" >> /usr/local/etc/php.ini
# RUN echo "variables_order=EGPCS" >> /usr/local/etc/php.ini
# RUN echo "memory_limit=1G" >> /usr/local/etc/php.ini
# RUN echo "max_execution_time=600" >> /usr/local/etc/php.ini
COPY php.ini /usr/local/etc/php/conf.d/99-sail.ini

# servidores dominios locais 
RUN mkdir -p /etc/apache2/from-host
# ... registre eles no windows: windows/system32/drivers/etc/hosts

# removendo a configuracao padrao
RUN mv /etc/apache2/sites-enabled/000-default.conf /etc/apache2/sites-enabled/000-default.conf.bkp

# configurando por padrao as diretrizes e permissoes
# root do servidor: /var/www
COPY ./apache2.conf /etc/apache2/apache2.conf
  
RUN a2enmod rewrite
