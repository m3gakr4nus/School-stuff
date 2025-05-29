# Verwende offizielles PHP 8.2 Apache Image
FROM php:8.2-apache
 
# PHP-Extensions und Tools installieren
RUN apt-get update && apt-get install -y \
    libpng-dev \
    libjpeg-dev \
    libfreetype6-dev \
    libzip-dev \
    libicu-dev \
    libxml2-dev \
    unzip \
    nano \
&& docker-php-ext-configure gd \
&& docker-php-ext-install \
        gd \
        mysqli \
        pdo \
        pdo_mysql \
        zip \
        intl \
        soap \
        exif \
        opcache
 
# Fehlerausgabe reduzieren
RUN echo "opcache.enable=1\nopcache.enable_cli=1" > /usr/local/etc/php/conf.d/opcache.ini \
&& echo "max_input_vars=5000" > /usr/local/etc/php/conf.d/input-vars.ini \
&& echo "display_errors=Off" > /usr/local/etc/php/conf.d/moodle-errors.ini \
&& echo "error_reporting=E_ALL & ~E_DEPRECATED & ~E_STRICT & ~E_NOTICE" >> /usr/local/etc/php/conf.d/moodle-errors.ini
 
# Moodle 5.0 herunterladen und entpacken
WORKDIR /var/www/html
#RUN curl -L -o moodle.tgz https://download.moodle.org/download.php/direct/stable401/moodle-4.1.2.tgz \
#RUN curl -L -o moodle.tgz https://download.moodle.org/download.php/direct/stable402/moodle-4.2.3.tgz \
RUN curl -L -o moodle.tgz https://download.moodle.org/download.php/direct/stable500/moodle-5.0.tgz \
&& tar -xzf moodle.tgz --strip-components=1 \
&& rm moodle.tgz
 
# Dateiberechtigungen setzen
RUN chown -R www-data:www-data /var/www/html
RUN chmod 755 /var/www/html -R

EXPOSE 80
CMD ["apache2-foreground"]
