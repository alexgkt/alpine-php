FROM smebberson/alpine-base
MAINTAINER Alex Goh <alex.goh@commercecraft.com.my>

# Environments
ENV TIMEZONE	Asia/Kuala_Lumpur

RUN apk add --update-cache --repository http://dl-cdn.alpinelinux.org/alpine/edge/testing/ --allow-untrusted \
	openssl \
	tzdata \
	curl \
	nginx \
   	php5-fpm \
	php5-opcache \
	php5-apcu \
	php5-ctype \
	php5-json \
	php5-xml \
	php5-xmlreader \
	php5-zlib \
	php5-curl \
	php5-pdo \
	php5-phar \
	php5-openssl \
    	php5-pdo_mysql \
	php5-mysqli \
    	php5-gd \	
	php5-iconv \
	php5-bcmath \
	php5-mcrypt && \
	#php-redis && \
    cp /usr/share/zoneinfo/${TIMEZONE} /etc/localtime && \
    echo "${TIMEZONE}" > /etc/timezone && \
    apk del tzdata && \
    rm -rf /var/cache/apk/*

RUN curl -sS https://getcomposer.org/installer | php -- --install-dir=/usr/local/bin --filename=composer && \
    composer global require "hirak/prestissimo:^0.3"
    #cp /etc/php/conf.d/redis.ini /etc/php5/conf.d && \
    #cp /usr/lib/php/modules/redis.so /usr/lib/php5/modules/redis.so && \
    #rm -rf /etc/php && \
    #rm -rf /usr/lib/php

RUN mkdir /tmp/nginx && \
    mkdir /etc/nginx/sites-available && \
    mkdir /var/log/php-fpm
#usermod -u 1000 www-data

ADD scripts /usr/bin/

RUN chmod +x /usr/bin/nginx-restart && chmod +x /usr/bin/php-fpm-restart

ADD conf/nginx.conf /etc/nginx/

ADD conf/php-fpm.conf /etc/php5/

ADD conf/default.vhost /etc/nginx/sites-available/

ADD services.d /etc/services.d/

WORKDIR /app

EXPOSE 80 443
