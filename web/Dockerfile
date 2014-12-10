FROM ubuntu:latest
MAINTAINER Ronny Laborius <ronny@laborius.org>

RUN apt-get update
RUN apt-get --force-yes -y -q install apache2 php5 php5-mysql

ENV APACHE_RUN_USER www-data
ENV APACHE_RUN_GROUP www-data
ENV APACHE_LOG_DIR /var/log/apache2
ENV APACHE_LOCK_DIR /var/lock/apache2
ENV APACHE_PID_FILE /var/run/apache2.pid

EXPOSE 80

CMD /usr/sbin/apache2ctl -D FOREGROUND
