FROM php:7.4-apache

# Gerekli PHP uzantılarını yükle
RUN apt-get update && apt-get install -y \
    libpng-dev \
    libjpeg-dev \
    libfreetype6-dev \
    libicu-dev \
    libxml2-dev \
    && docker-php-ext-configure gd --with-freetype --with-jpeg \
    && docker-php-ext-install gd pdo pdo_mysql intl xml

# Apache modlarını etkinleştir
RUN a2enmod rewrite ssl

# SSL konfigürasyon dosyasını kopyala
COPY default-ssl.conf /etc/apache2/sites-available/default-ssl.conf

# SSL siteyi etkinleştir
RUN a2ensite default-ssl

# PHP konfigürasyon dosyasını kopyala
COPY php.ini /usr/local/etc/php/

CMD ["apache2-foreground"]
