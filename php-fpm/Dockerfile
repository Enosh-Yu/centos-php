#php-fpm
FROM centos:6.8
MAINTAINER Enosh Yu

RUN rpm -i http://dl.fedoraproject.org/pub/epel/6/x86_64/epel-release-6-8.noarch.rpm
RUN rpm -Uvh http://mirror.webtatic.com/yum/el6/latest.rpm

#RUN yum -y install php php-fpm php-gd php-ldap \
#   php-sqlite php-pgsql php-pear php-mysql \
#   php-mcrypt php-xcache php-xml php-xmlrpc

RUN yum install -y php56w php56w-cli php56w-common php56w-mbstring php56w-mcrypt php56w-mysql php56w-pdo php56w-fpm php56w-xml

RUN sed -i '/^listen/c \
listen = 0.0.0.0:9000' /etc/php-fpm.d/www.conf

RUN sed -i 's/^listen.allowed_clients/;listen.allowed_clients/' /etc/php-fpm.d/www.conf

RUN mkdir -p /srv/http && \
    echo "<?php phpinfo(); ?>" > /srv/http/index.php && \
    chown -R apache:apache /srv/http

EXPOSE 9000
VOLUME /srv/http
ENTRYPOINT ["php-fpm","-F"]