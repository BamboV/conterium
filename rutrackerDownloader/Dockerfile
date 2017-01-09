FROM composer/composer:php7

RUN apt-get update && \
    apt-get install --no-install-recommends --no-install-suggests -y \
        ca-certificates \
        git && \
    apt-get clean

ARG RUTRACKER_LOGIN
ARG RUTRACKER_PASSWORD

RUN git clone https://github.com/BamboV/rutrackerDownloader.git /var/www/web && \
    chmod 777 /var/www/web/storage -R && \
    chmod 777 /var/www/web/var/logs -R && \
    chmod 777 /var/www/web/var/sessions -R && \
    cd /var/www/web && composer install && \
    sed -i -e 's/rutracker_login: null/rutracker_login: '${RUTRACKER_LOGIN}'/' /var/www/web/app/config/parameters.yml && \
    sed -i -e 's/rutracker_password: null/rutracker_password: '${RUTRACKER_PASSWORD}'/' /var/www/web/app/config/parameters.yml && \
    /var/www/web/bin/console cache:warmup --env=prod && \
    chmod 777 /var/www/web/var/cache -R

VOLUME /var/www/web