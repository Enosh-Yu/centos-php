#apache2
FROM webdevops/apache:centos-7

MAINTAINER Enosh Yu

ARG PHP_SOCKET="php-fpm:9000"

ENV WEB_PHP_SOCKET=$PHP_SOCKET

ENV WEB_DOCUMENT_ROOT=/var/www/html

EXPOSE 80 443

WORKDIR /var/www

ENTRYPOINT ["/opt/docker/bin/entrypoint.sh"]

CMD ["supervisord"]