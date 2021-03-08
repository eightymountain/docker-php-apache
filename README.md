# docker-php-apache

#### version

- centos 7

- apahce 2.4.6

- php 7.3.27

- maria 10.? -> X

#### setup

```bash
cp .env.example .env

docker-compose up -d --build
```

#### windows options

edit file

`C:\Windows\System32\drivers\etc\hosts`

add this

`127.0.0.1 localdev.test`
