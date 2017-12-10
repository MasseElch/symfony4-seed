FROM php:7.2-fpm-alpine

MAINTAINER MasseElch <info@masseelch.com>

# Install php extensions
RUN apk add --update icu-dev \
 && docker-php-ext-install mbstring pdo_mysql intl opcache \
 && rm -rf /var/cache/apk/*

# Install composer
ENV COMPOSER_HOME /root/.composer
RUN apk --update add curl \
 && curl -sS https://getcomposer.org/installer | php -- --install-dir=/usr/bin --filename=composer \
 && apk del curl \
 && rm -rf /var/cache/apk/*

# Install zsh and oh-my-zsh
RUN apk add --update python build-base git zsh \
 && wget https://github.com/robbyrussell/oh-my-zsh/raw/master/tools/install.sh -O - | zsh || true \
 && apk del python build-base git \
 && rm -rf /var/cache/apk/*

# Install git and ssh
RUN apk add --update git openssh-client \
 && rm -rf /var/cache/apk/*
