FROM alpine:3.16

# Setup apache and php
RUN apk --no-cache --update \
    add apache2 \
    apache2-ssl \
    curl \
    php8-apache2 \
    php8-bcmath \
    php8-bz2 \
    php8-calendar \
    php8-common \
    php8-ctype \
    php8-curl \
    php8-dom \
    php8-gd \
    php8-iconv \
    php8-mbstring \
    php8-mysqli \
    php8-mysqlnd \
    php8-openssl \
    php8-pdo_mysql \
    php8-pdo_pgsql \
    php8-pdo_sqlite \
    php8-phar \
    php8-session \
    php8-xml \
    php-tokenizer \
    php-xmlwriter \
    && curl -L -o /tmp/phpunit https://phar.phpunit.de/phpunit-9.5.9.phar  \
    && install /tmp/phpunit /usr/local/bin  \
    && mkdir /htdocs

#     && echo "<?php echo 'hello' .PHP_EOL; phpinfo(); "  | tee /htdocs/index.php

EXPOSE 80 443
HEALTHCHECK CMD wget -q --no-cache --spider localhost

ADD docker-entrypoint.sh /
ENTRYPOINT ["/docker-entrypoint.sh"]


# Copy application files at the end to be able to reuse cache layers
ADD app/ /htdocs


