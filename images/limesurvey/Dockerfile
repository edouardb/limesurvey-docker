FROM ubuntu:latest

MAINTAINER Edouard BONLIEU "ebonlieu@gmail.com"

# Update system
ENV DEBIAN_FRONTEND=noninteractive
RUN apt-get -q -y update \
	&& apt-get upgrade -q -y \
	&& apt-get install -q -y nginx php-fpm php-gd php-imap php-ldap php-zip php-pgsql php-mbstring php-xml zlibc zlib1g zlib1g-dev wget supervisor \
	&& apt-get clean


# Configure app
RUN adduser --disabled-password --shell /bin/bash --gecos 'LimeSurvey user' limesurvey \
	&& install -d -m 755 -o limesurvey -g limesurvey /var/www/limesurvey

RUN wget -qO limesurvey.tar.gz http://download.limesurvey.org/latest-stable-release/limesurvey2.53+161004.tar.gz && \
	tar -xzf limesurvey.tar.gz && \
	rm -rf /var/www && \
	mv limesurvey /var/www

RUN sed -i -e "s/;extension=php_xmlrpc.dll/extension=php_xmlrpc.dll/g" /etc/php/7.0/fpm/php.ini

RUN mkdir -p /var/run/php && \
	mkdir -p /var/www/tmp/assets

RUN echo "daemon off;" >> /etc/nginx/nginx.conf

# Patch rootfs
ADD ./patches/etc/ /etc/

RUN  chown -R www-data:www-data /var/www

CMD ["/usr/bin/supervisord"]
