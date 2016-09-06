#workspace
FROM centos:6.8
MAINTAINER Enosh Yu

RUN rpm -i http://dl.fedoraproject.org/pub/epel/6/x86_64/epel-release-6-8.noarch.rpm
RUN rpm -Uvh http://mirror.webtatic.com/yum/el6/latest.rpm

# install php
# RUN yum install -y php php-mysql php-devel php-gd php-pecl-memcache php-pspell php-snmp php-xmlrpc php-xml
RUN yum install -y php56w php56w-cli php56w-common php56w-mbstring php56w-mcrypt php56w-mysql php56w-pdo php56w-fpm php56w-xml

# Install composer and add its bin to the PATH.
RUN curl -s http://getcomposer.org/installer | php && \
    mv composer.phar /usr/local/bin/composer
EXPOSE 22

WORKDIR /var/www
