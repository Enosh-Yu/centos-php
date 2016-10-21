FROM centos:6.8
MAINTAINER Thatcher Peskens <thatcher@koffiedik.net>

# install http
RUN rpm -Uvh http://dl.fedoraproject.org/pub/epel/6/x86_64/epel-release-6-8.noarch.rpm
RUN rpm -Uvh http://mirror.webtatic.com/yum/el6/latest.rpm

# install httpd
RUN yum -y install httpd vim-enhanced bash-completion unzip

# install php
# RUN yum install -y php php-mysql php-devel php-gd php-pecl-memcache php-pspell php-snmp php-xmlrpc php-xml
# RUN yum install -y php56w php56w-cli php56w-common php56w-mbstring php56w-mcrypt php56w-mysqlnd php56w-pdo php56w-fpm php56w-xml
RUN yum install -y php56w php56w-cli php56w-common php56w-mbstring php56w-mcrypt php56w-mysql php56w-pdo php56w-fpm php56w-xml php56w-gd
# install supervisord
RUN yum install -y python-pip && pip install "pip>=1.4,<1.5" --upgrade
RUN pip install supervisor

# install sshd
RUN yum install -y openssh-server openssh-clients passwd

RUN ssh-keygen -q -N "" -t dsa -f /etc/ssh/ssh_host_dsa_key && ssh-keygen -q -N "" -t rsa -f /etc/ssh/ssh_host_rsa_key 
RUN sed -ri 's/UsePAM yes/UsePAM no/g' /etc/ssh/sshd_config && echo 'root:changeme' | chpasswd

#install composer
RUN curl -sS https://getcomposer.org/installer | php
RUN mv composer.phar /usr/local/bin/composer

RUN sed -i "s/DirectoryIndex index.php/DirectoryIndex index.php index.htm index.html/g" /etc/httpd/conf.d/php.conf
RUN echo "AddType application/x-httpd-php .htm .html" >> /etc/httpd/conf.d/php.conf

ADD phpinfo.php /var/www/html/
ADD supervisord.conf /etc/
EXPOSE 80 443
CMD ["supervisord", "-n"]