# CENTOS 7 BASE IMAGE
# This Dockerfile is used to create a web server image based on CentOS 7
FROM centos:7
LABEL maintainer="rortizs@miumg.edu.gt"

# install epel-release and httpd, nginx, php, php-mysqlnd, php-fpm, php-mbstring, php-xml, php-gd, php-zip, php-curl
RUN yum -y install epel-release && \
    yum -y update && \
        nginx \
        php-fpm \
        php-cli \
        php-mysqlnd \
        php-gd \
        php-ldap \
        php-xml \
        php-mbstring \
        php-json \
        php-zip \
        php-curl  && \
    yum clean all && \
    mkdir -p /var/www/html && \
    chown -R nginx:nginx /var/www/html


    # Copy the nginx configuration file
    COPY config/nginx.conf /etc/nginx/nginx.conf
    COPY config/default.conf /etc/nginx/conf.d/default.conf
    COPY config/www.conf /etc/php-fpm.d/www.conf

    # script startup.sh
    COPY start.sh /start.sh
    RUN chmod +x /start.sh

    # port 80
    EXPOSE 80

    # START COMMAND
    CMD ["/start.sh"]
