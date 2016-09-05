#mysql
FROM centos:6.8
MAINTAINER Enosh Yu

# install mysql
RUN yum install -y mysql mysql-server
RUN echo "NETWORKING=yes" > /etc/sysconfig/network
# start mysqld to create initial tables
RUN service mysqld start

# install supervisord
RUN yum install -y python-pip && pip install "pip>=1.4,<1.5" --upgrade
RUN pip install supervisor

CMD ["mysqld"]

EXPOSE 3306