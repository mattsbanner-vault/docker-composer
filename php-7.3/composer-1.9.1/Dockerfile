FROM ubuntu:18.04

LABEL maintainer = "Matt Banner <matt@banner.wtf>"

ENV DEBIAN_FRONTEND noninteractive
ENV PHP_VERSION 7.3
ENV COMPOSER_VERSION 1.9.1

RUN \
    apt-get update && \
    apt-get install -y software-properties-common && \
    add-apt-repository ppa:ondrej/php && \
    apt-get install -y \
        php${PHP_VERSION}-fpm \
        git \
        libargon2-0 \
        libedit2 \
        libpcre2-8-0 \
        libsodium23 \
        php-common \
        php-pear \
        php${PHP_VERSION}-cli \
        php${PHP_VERSION}-common \
        php${PHP_VERSION}-json \
        php${PHP_VERSION}-opcache \
        php${PHP_VERSION}-readline \
        php${PHP_VERSION}-simplexml \
        php${PHP_VERSION}-mbstring \
        php${PHP_VERSION}-curl \
        php${PHP_VERSION}-zip \
        php${PHP_VERSION}-xdebug \
        php${PHP_VERSION}-dev \
        php${PHP_VERSION}-mysql \
        php${PHP_VERSION}-xml \
        php${PHP_VERSION}-sqlite3 \
        php${PHP_VERSION}-bcmath \
        php${PHP_VERSION}-soap \
        php${PHP_VERSION}-gd \
        psmisc \
        tzdata \
        unzip && \
    php -r "readfile('https://getcomposer.org/installer');" | php -- --install-dir=/usr/bin/ --filename=composer --version=${COMPOSER_VERSION} && \
    composer global require hirak/prestissimo && \
    apt-get remove -y software-properties-common && \
    apt-get autoremove -y && \
    rm -rf /var/lib/apt/lists/* /var/cache/apt/*

VOLUME ["/app"]
WORKDIR /app

CMD ["-"]
ENTRYPOINT ["composer", "--ansi"]