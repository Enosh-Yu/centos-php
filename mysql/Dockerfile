# "ported" by Adam Miller <maxamillion@fedoraproject.org> from
#   https://github.com/fedora-cloud/Fedora-Dockerfiles
#
# Originally written for Fedora-Dockerfiles by
#   scollier <scollier@redhat.com>

FROM centos:6.8
MAINTAINER The CentOS Project <cloud-ops@centos.org>

ARG MYSQL_ROOT_PASSWORD="secret"
ENV MYSQL_ROOT_PASSWORD=$MYSQL_ROOT_PASSWORD

ARG MYSQL_DATABASE="my_php_app"
ENV MYSQL_DATABASE=$MYSQL_DATABASE

ARG MYSQL_USER="my_php_app"
ENV MYSQL_USER=$MYSQL_USER

ARG MYSQL_PASSWORD="pAsSwOrD"
ENV MYSQL_PASSWORD=$MYSQL_PASSWORD

RUN yum -y update; yum clean all
RUN yum -y install epel-release; yum clean all
RUN yum -y install mysql-server mysql pwgen supervisor bash-completion psmisc net-tools; yum clean all

ADD ./start.sh /start.sh
ADD ./config_mysql.sh /config_mysql.sh
ADD ./supervisord.conf /etc/supervisord.conf

# RUN echo %sudo	ALL=NOPASSWD: ALL >> /etc/sudoers

RUN chmod 755 /start.sh
RUN chmod 755 /config_mysql.sh
RUN /config_mysql.sh

EXPOSE 3306

CMD ["/bin/bash", "/start.sh"]