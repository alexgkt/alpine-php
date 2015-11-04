FROM alexgkt/alpine-php
MAINTAINER Alex Goh <alex.goh@commercecraft.com.my>

RUN echo http://dl-4.alpinelinux.org/alpine/edge/main > /tmp/new_repo && \
    apk add --update --repositories-file /tmp/new_repo -u php-ctype

RUN composer self-update && \
    composer global require drush/drush:7.* && \
    ln -s /root/.composer/vendor/drush/drush/drush /usr/local/bin/drush && \
    drush dl drupal --destination=/app --drupal-project-rename=www


