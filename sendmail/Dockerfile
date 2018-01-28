FROM centos:7

MAINTAINER Faqueer Tanvir Ahmed "ftahmed@gmail.com"

WORKDIR /etc/mail

RUN set -e && \
 yum -y update
RUN set -e && \
 yum install -y sendmail sendmail-cf cyrus-sasl-plain
RUN set -e && \
 yum install -y make
RUN set -e && \
 yum install -y mailx
RUN set -e && \
 yum install -y openssl
RUN set -e && \
 yum install -y patch

#COPY sendmail.mc /etc/mail/sendmail.mc
COPY sendmail.mc.patch /etc/mail/sendmail.mc.patch
RUN patch sendmail.mc sendmail.mc.patch

RUN make sendmail.cf && \
 echo "Connect:172 RELAY" >> access && \
 echo "Connect:10 RELAY" >> access && \
 make

COPY sendmail.pem /etc/pki/tls/certs/sendmail.pem
#RUN chmod 600 /etc/pki/tls/certs/sendmail.pem

EXPOSE 25
EXPOSE 465

CMD /usr/lib/sendmail -bD -X /proc/self/fd/1
#CMD /bin/bash
