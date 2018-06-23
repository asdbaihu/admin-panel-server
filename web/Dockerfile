FROM centos:latest
RUN yum -y update
RUN curl 'https://setup.ius.io/' -o setup-ius.sh -k
RUN bash setup-ius.sh
RUN yum -y update
RUN yum -y install supervisor git nginx php71u php71u-json php71u-pgsql php71u-mysqlnd php71u-cli php71u-fpm-nginx php71u-mbstring php71u-dom

RUN mkdir -p /var/www
VOLUME ["/var/www"]

#NGINX
ADD nginx/nginx.conf /etc/nginx/nginx.conf
RUN mkdir -p /etc/nginx/sites-enabled

#PHP-FPM
ADD php-fpm/www.conf /etc/php-fpm.d/www.conf

#COMPOSER
RUN curl -o composer.phar https://getcomposer.org/composer.phar
RUN chmod +x composer.phar
RUN mv composer.phar /usr/local/bin/composer

#SUPERVISOR
RUN mkdir -p /var/log/supervisor
ADD supervisor/supervisord.conf /etc/supervisor/conf.d/supervisord.conf

RUN cp /usr/share/zoneinfo/Europe/Moscow /etc/localtime

WORKDIR /var/www

CMD ["/usr/bin/supervisord", "-c", "/etc/supervisor/conf.d/supervisord.conf"]
