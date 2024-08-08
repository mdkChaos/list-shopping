FROM php:8.3-fpm

# Оновлюємо пакети та встановлюємо необхідні залежності
RUN apt update && apt install -y \
      apt-utils \
      libpq-dev \
      libpng-dev \
      libzip-dev \
      zip unzip \
      git \
    && docker-php-ext-install pdo_mysql bcmath gd zip \
    && apt clean \
    && rm -rf /var/lib/apt/lists/* /tmp/* /var/tmp/*

# Копіюємо налаштування PHP
COPY ./_docker/api/php.ini /usr/local/etc/php/conf.d/php.ini

# Встановлюємо Composer
ENV COMPOSER_ALLOW_SUPERUSER=1
RUN curl -sS https://getcomposer.org/installer | php -- \
    --filename=composer \
    --install-dir=/usr/local/bin

# Встановлюємо робочу директорію
WORKDIR /var/www/