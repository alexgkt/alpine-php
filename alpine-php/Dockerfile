FROM smebberson/alpine-base
MAINTAINER Alex Goh <alex.goh@commercecraft.com.my>

# Environments
ENV TIMEZONE	Asia/Kuala_Lumpur

RUN apk add --update tzdata && \
    cp /usr/share/zoneinfo/${TIMEZONE} /etc/localtime && \
    echo "${TIMEZONE}" > /etc/timezone && \
    apk add --update \
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
	php5-mcrypt && \
    rm -rf /var/cache/apk/* && \
    apk del tzdata && \

ADD conf/nginx.conf /etc/nginx/
ADD conf/php-fpm.conf /etc/php/

ADD nginx /etc/services.d/nginx/
ADD php-fpm /etc/services.d/php-fpm/

VOLUME /app

EXPOSE 80
