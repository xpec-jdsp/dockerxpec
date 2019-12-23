FROM ubuntu:16.04

RUN apt-get update \
    && apt-get -y install git apache2 nano mysql-client \
    && a2enmod rewrite \
    && a2enmod headers \
    && export LANG=en_US.UTF-8 \
    && apt-get update \
    && apt-get install -y software-properties-common \
    && apt-get install -y language-pack-en-base \
    && LC_ALL=en_US.UTF-8 add-apt-repository ppa:ondrej/php \
    && apt-get update \
    && apt-get -y install php7.1 php7.1-curl php7.1-intl php7.1-gd php7.1-dom php7.1-mcrypt php7.1-iconv php7.1-xsl php7.1-mbstring php7.1-ctype php7.1-zip php7.1-pdo php7.1-xml php7.1-bz2 php7.1-calendar php7.1-exif php7.1-fileinfo php7.1-json php7.1-mysqli php7.1-mysql php7.1-posix php7.1-tokenizer php7.1-xmlwriter php7.1-xmlreader php7.1-phar php7.1-soap php7.1-mysql php7.1-fpm php7.1-bcmath libapache2-mod-php7.1 \
    && sed -i -e"s/^memory_limit\s*=\s*128M/memory_limit = 2048M/" /etc/php/7.1/apache2/php.ini \
    && sed -i -e"s/^max_input_time\s*=\s*60/max_input_time = 3600/" /etc/php/7.1/apache2/php.ini \
    && sed -i -e"s/^max_execution_time\s*=\s*30/max_execution_time = 1800/" /etc/php/7.1/apache2/php.ini \
    ## Activar el opcache, aun no lo pruebo && sed -i -e"s/^;opcache.enable=1/opcache.enable=1/" /etc/php/7.1/apache2/php.ini \
    && rm /var/www/html/* \
    && sed -i "s/None/all/g" /etc/apache2/apache2.conf \
    && sed -i "s/80/8080/g" /etc/apache2/ports.conf /etc/apache2/sites-enabled/000-default.conf \
    && apt-get install -y supervisor \
    && mkdir -p /var/log/supervisor

ENV APACHE_RUN_USER    www-data
ENV APACHE_RUN_GROUP   www-data
ENV APACHE_PID_FILE    /var/run/apache2.pid
ENV APACHE_RUN_DIR     /var/run/apache2
ENV APACHE_LOCK_DIR    /var/lock/apache2
ENV APACHE_LOG_DIR     /var/log/apache2
ENV LANG               C

WORKDIR /var/www/html

CMD ["/usr/bin/supervisord"]

