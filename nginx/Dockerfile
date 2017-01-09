FROM nginx:alpine

ADD nginx.conf /etc/nginx/conf.d/

ARG PHP_UPSTREAM=fpm

RUN apk update \
    && apk upgrade \
    && apk add --no-cache bash \
    && adduser -D -H -u 1000 -s /bin/bash www-data \
    && rm /etc/nginx/conf.d/default.conf \
    && echo "upstream php-upstream { server ${PHP_UPSTREAM}:9000; }" > /etc/nginx/conf.d/upstream.conf

CMD ["nginx", "-g", "daemon off;"]

EXPOSE 80 443