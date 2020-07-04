FROM ubuntu:latest

RUN apt-get update
RUN apt-get -y upgrade

# Install apache
RUN DEBIAN_FRONTEND=noninteractive apt-get -y install apache2 curl 



# Manually set up the apache environment variables
ENV APACHE_RUN_USER www-data
ENV APACHE_RUN_GROUP www-data
ENV APACHE_LOG_DIR /var/log/apache2
ENV APACHE_LOCK_DIR /var/lock/apache2
ENV APACHE_PID_FILE /var/run/apache2.pid

EXPOSE 80


# Update the default apache site with the config we created.
ADD apache-config.conf /etc/apache2/sites-enabled/000-default.conf
ADD index.html /var/www/html/index.html
# By default, simply start apache.
CMD /usr/sbin/apache2ctl -D FOREGROUND
