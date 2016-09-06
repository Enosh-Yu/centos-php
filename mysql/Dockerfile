#mysql
FROM centos:6.8
MAINTAINER Enosh Yu

RUN rpm -Uvh http://dl.fedoraproject.org/pub/epel/6/x86_64/epel-release-6-8.noarch.rpm
RUN rpm -Uvh http://mirror.webtatic.com/yum/el6/latest.rpm

# install mysql
RUN yum install -y mysql mysql-server
RUN echo "NETWORKING=yes" > /etc/sysconfig/network
# start mysqld to create initial tables
RUN service mysqld start

# install supervisord
RUN yum install -y python-pip && pip install "pip>=1.4,<1.5" --upgrade
RUN pip install supervisor

CMD ["supervisord"]

EXPOSE 3306