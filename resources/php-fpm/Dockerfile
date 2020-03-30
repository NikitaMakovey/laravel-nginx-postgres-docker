FROM phpdockerio/php73-fpm:latest
WORKDIR "/var/www/src"

# Fix debconf warnings upon build
ARG DEBIAN_FRONTEND=noninteractive

# Install selected extensions and other stuff
RUN apt-get update \
    && apt-get -y --no-install-recommends install  php7.3-pgsql php7.3-gd \
    && apt-get clean; rm -rf /var/lib/apt/lists/* /tmp/* /var/tmp/* /usr/share/doc/*

# Install git
RUN apt-get update \
    && apt-get -y install git \
    && apt-get clean; rm -rf /var/lib/apt/lists/* /tmp/* /var/tmp/* /usr/share/doc/*

# Install curl
RUN apt-get -y install curl

# Install node.js and npm
RUN curl -sL https://deb.nodesource.com/setup_12.x | bash \
    && apt-get -y install nodejs \
    && node -v \
    && npm -v

# Install composer
RUN curl -sS https://getcomposer.org/installer | php -- \
    --filename=composer \
    --install-dir=/usr/local/bin && \
    echo "alias composer='composer'" >> /root/.bashrc && \
    composer
