FROM centos:7

MAINTAINER Faqueer Tanvir Ahmed "ftahmed@gmail.com"

RUN set -e && \
 yum install -y openssl
RUN set -e && \
 yum install -y squid

# Redirect logs to stdout for the container
#RUN ln -sf /dev/stdout /var/log/squid/access.log

EXPOSE 80
EXPOSE 443

VOLUME /etc/squid

CMD /usr/sbin/squid -N -f /etc/squid/squid.conf
#CMD /bin/bash
