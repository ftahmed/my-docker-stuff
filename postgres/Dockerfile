FROM centos:centos7
MAINTAINER Faqueer Tanvir Ahmed <ftahmed@gmail.com>

RUN yum -y update; yum clean all
RUN yum -y install sudo epel-release; yum clean all
RUN yum -y install https://download.postgresql.org/pub/repos/yum/9.6/redhat/rhel-7-x86_64/pgdg-centos96-9.6-3.noarch.rpm
RUN yum -y install postgresql96-server.x86_64 postgresql96-contrib.x86_64 postgresql96-devel.x86_64

ADD postgresql-9.6.service /etc/systemd/system/postgresql-9.6.service
RUN systemctl daemon-reload
RUN /usr/pgsql-9.6/bin/postgresql96-setup initdb

VOLUME ["/var/lib/pgsql"]

EXPOSE 5432

CMD ["systemctl", "start", "postgresql-9.4.service"]
