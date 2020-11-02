FROM phpdockerio/php74-fpm:latest
WORKDIR "/application"

# Fix debconf warnings upon build
ARG DEBIAN_FRONTEND=noninteractive

RUN apt-get update && apt-get install -y --no-install-recommends apt-utils

# Install selected extensions and other stuff
RUN apt-get update \
    && apt-get -y --no-install-recommends install make gcc php7.4-dev imagemagick php7.4-mysql php7.4-pgsql php7.4-gd php7.4-soap php7.4-imagick php-redis libpng-dev \
    && apt-get clean; rm -rf /var/lib/apt/lists/* /tmp/* /var/tmp/* /usr/share/doc/*

RUN apt-get install -y curl \
    && curl -sL https://deb.nodesource.com/setup_10.x | bash - \
    && apt-get install -y nodejs \
    && curl -L https://www.npmjs.com/install.sh | sh

# Install git inside container
RUN apt-get update \
    && apt-get -y install git \
    && apt-get clean; rm -rf /var/lib/apt/lists/* /tmp/* /var/tmp/* /usr/share/doc/*

RUN apt-get update && apt-get install -y --no-install-recommends --no-install-suggests supervisor

# RUN npm install -g pngquant-bin

RUN apt-get install libpng-dev

# Fix laravel permissions
RUN usermod -u 1000 www-data

CMD ["/usr/bin/supervisord", "-n", "-c", "/etc/supervisor/conf.d/laravel-worker.conf"]