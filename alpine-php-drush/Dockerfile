FROM alexgkt/alpine-php
MAINTAINER Alex Goh <alex.goh@commercecraft.com.my>

RUN apk --update add mariadb-client && \
    composer self-update && \
    composer global require drush/drush && \
    ln -s /root/.composer/vendor/drush/drush/drush /usr/local/bin/drush


