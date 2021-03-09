FROM centos:7

RUN yum -y update

RUN curl -L -s http://repos.fedorapeople.org/repos/jkaluza/httpd24/epel-httpd24.repo > /etc/yum.repos.d/epel-httpd24.repo
RUN yum -y install httpd

RUN yum -y install https://rpms.remirepo.net/enterprise/remi-release-7.rpm 
RUN yum -y install epel-release yum-utils

RUN yum-config-manager --disable remi-php54  
RUN yum-config-manager --enable remi-php73

# RUN yum install -y php

RUN yum install -y php php-cli php-fpm php-mysqlnd php-zip php-devel php-gd php-mcrypt php-mbstring php-curl php-xml php-pear php-bcmath php-json

RUN sed -i 's/upload_max_filesize = 2M/upload_max_filesize = 100M/' /etc/php.ini
RUN sed -i 's/post_max_size = 8M/post_max_size = 100M/' /etc/php.ini

# Fix timezone issue
ENV TZ=Asia/Seoul
RUN ln -snf /usr/share/zoneinfo/$TZ /etc/localtime && echo $TZ > /etc/timezone

COPY ./httpd.conf /etc/httpd/conf/
COPY ./vhosts.conf /etc/httpd/conf.d/

ENV APACHE_LOG_DIR /var/log/httpd
RUN mkdir -p $APACHE_LOG_DIR

RUN systemctl enable httpd

EXPOSE "80"

CMD ["httpd", "-D", "FOREGROUND"]