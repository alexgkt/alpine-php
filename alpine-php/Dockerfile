FROM justcontainers/base-alpine
MAINTAINER Alex Goh <alex.goh@commercecraft.com.my>

RUN echo http://dl-4.alpinelinux.org/alpine/edge/main > /tmp/new_repo && \
    apk add --update --repositories-file /tmp/new_repo -u \
    musl nginx ca-certificates curl acl \
    php-fpm php-json php-xml php-xmlreader php-zlib php-curl php-pdo php-phar php-openssl \
    php-pdo_mysql php-mysqli \
    php-gd php-iconv php-mcrypt && \
    rm -rf /var/cache/apk/* && \
    curl -sS https://getcomposer.org/installer | php -- --install-dir=/usr/local/bin --filename=composer

RUN mkdir -p /tmp/nginx && chown nginx /tmp/nginx

ADD conf/nginx.conf /etc/nginx/
ADD conf/php-fpm.conf /etc/php/

ADD nginx /etc/services.d/nginx/
ADD php-fpm /etc/services.d/php-fpm/

ENV USER app
ENV UID 1001

RUN adduser -h /app -G www-data -u ${UID} ${USER} && \
    setfacl -m g:www-data:rwx /app

ADD www /app/www

VOLUME /app/www

EXPOSE 80
