FROM php:8.3-fpm

ARG TZ

# Set the timezone
RUN apt-get update && apt-get install -y tzdata && \
    ln -snf /usr/share/zoneinfo/${TZ} /etc/localtime && \
    echo ${TZ} > /etc/timezone && \
    apt-get clean && rm -rf /var/lib/apt/lists/*

RUN apt-get update && apt-get install -y \
    acl \
    msmtp \
    bash \
    perl \
    wget \
    curl \
    git \
    unzip \
    graphviz \
    imagemagick \
    libaio1 \
    libfreetype6-dev \
    libicu-dev \
    libzip-dev \
    libmagickwand-dev \
    libpng-dev \
    libpq-dev \
    librabbitmq-dev \
    libwebp-dev \
    libxpm-dev \
    libonig-dev \
    libjpeg-dev \
    openvpn \
    nano \
    zip \
    nodejs \
    npm \
    openssl \
    libssl-dev \
    libhiredis-dev


RUN docker-php-ext-install \
    opcache \
    exif \
    intl \
    gettext \
    bcmath \
    pdo \
    mysqli \
    pdo_mysql \
    mbstring \
    soap \
    xml \
    gd \
    zip

COPY --chmod=755 ./.docker/supervisord/entrypoint.sh /etc/entrypoint.sh
COPY --chmod=755 . /var/www/core

ARG HOST_UID
ARG USER_NAME
RUN adduser --disabled-password --gecos "" --uid $HOST_UID $USER_NAME

USER $USER_NAME

WORKDIR /var/www/core
ENTRYPOINT ["/etc/entrypoint.sh"]