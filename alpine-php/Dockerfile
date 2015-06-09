FROM justcontainers/base-alpine
MAINTAINER Alex Goh <alex.goh@commercecraft.com.my>

RUN echo http://dl-4.alpinelinux.org/alpine/edge/main > /tmp/new_repo && \
    apk add --update --repositories-file /tmp/new_repo -u \
    musl nginx ca-certificates curl \
    php-fpm php-json php-zlib php-xml php-pdo php-phar php-openssl \
    php-pdo_mysql php-mysqli \
    php-gd php-iconv php-mcrypt && \
    rm -rf /var/cache/apk/* && \
    curl -sS https://getcomposer.org/installer | php -- --install-dir=/usr/local/bin --filename=composer

RUN mkdir -p /tmp/nginx && chown nginx /tmp/nginx && mkdir -p /app/logs/nginx && mkdir -p /app/logs/php-fpm

ADD conf/nginx.conf /etc/nginx/
ADD conf/php-fpm.conf /etc/php/

ADD nginx /etc/services.d/nginx/
ADD php-fpm /etc/services.d/php-fpm/

ADD www /app/www

EXPOSE 80
VOLUME ["/app"]
