FROM php:7.1.24-apache-jessie

RUN apt-get update && apt-get install -y \
    vim \
    cron

RUN touch /var/log/cron.log \
    && chmod 0644 /var/log/cron.log \
    && echo '* * * * * /var/www/html/bin/console cron:run 1>> /dev/null 2>&1' > /etc/cron.d/symfony \
    && crontab /etc/cron.d/symfony

RUN docker-php-ext-install \
    pdo_mysql \
    && a2enmod rewrite

COPY docker-php-entrypoint /usr/local/bin/

ENTRYPOINT ["docker-php-entrypoint"]
