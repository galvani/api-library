FROM php:7.2-fpm

MAINTAINER Jan Kozak <galvani78@gmail.com>

COPY web.pool.conf  /usr/local/etc/

RUN usermod -u 1000 www-data

RUN php -r "copy('https://getcomposer.org/installer', 'composer-setup.php');"
RUN php -r "if (hash_file('SHA384', 'composer-setup.php') === '544e09ee996cdf60ece3804abc52599c22b1f40f4323403c44d44fdfdd586475ca9813a858088ffbc1f233e9b180f061') { echo 'Installer verified'; } else { echo 'Installer corrupt'; unlink('composer-setup.php'); } echo PHP_EOL;"
RUN php composer-setup.php --install-dir=/usr/bin && chmod 755 /usr/bin/composer.phar
RUN php -r "unlink('composer-setup.php');"

EXPOSE 9000
CMD ["php-fpm", "-F"]