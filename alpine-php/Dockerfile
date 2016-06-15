FROM smebberson/alpine-base
MAINTAINER Alex Goh <alex.goh@commercecraft.com.my>

# Environments
ENV TIMEZONE	Asia/Kuala_Lumpur

RUN apk update && \
    apk upgrade && \
    apk add --update tzdata && \
    cp /usr/share/zoneinfo/${TIMEZONE} /etc/localtime && \
    echo "${TIMEZONE}" > /etc/timezone && \
    apk add --update \
	curl \
	nginx \
   	php-fpm \
	php-opcache \
	php-apcu \
	php-ctype \
	php-json \
	php-xml \
	php-xmlreader \
	php-zlib \
	php-curl \
	php-pdo \
	hp-phar \
	php-openssl \
    	php-pdo_mysql \
	php-mysqli \
    	php-gd \	
	php-iconv \
	php-mcrypt && \
    rm -rf /var/cache/apk/* && \
    apk del tzdata && \
    curl -sS https://getcomposer.org/installer | php -- --install-dir=/usr/local/bin --filename=composer && \
    mkdir -p /tmp/nginx && chown nginx /tmp/nginx && mkdir /var/log/php-fpm

ADD conf/nginx.conf /etc/nginx/
ADD conf/php-fpm.conf /etc/php/

ADD nginx /etc/services.d/nginx/
ADD php-fpm /etc/services.d/php-fpm/

VOLUME /app

EXPOSE 80
