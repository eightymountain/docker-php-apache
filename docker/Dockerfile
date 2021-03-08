FROM httpd:2.4

RUN apt-get update

RUN apt-get install -y php7.3 php7.3-cli php7.3-common zlib1g-dev libzip-dev

COPY ./httpd.conf /usr/local/apache2/conf/httpd.conf

EXPOSE "80"

CMD ["httpd"]
