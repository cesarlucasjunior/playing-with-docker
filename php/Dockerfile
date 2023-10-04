# image responsible for the image builder
FROM php:7.4-cli as builder
WORKDIR /var/www

RUN apt-get update && \
    apt-get install libzip-dev -y && \
    docker-php-ext-install zip

RUN php -r "copy('https://getcomposer.org/installer', 'composer-setup.php');" && \
    php composer-setup.php && \
    php -r "unlink('composer-setup.php');"

RUN php composer.phar create-project --prefer-dist laravel/laravel laravel

# image responsible for image otimization
FROM php:7.4-fpm-alpine
WORKDIR /var/www
RUN rm -rf ./html
# copying all the work done on the previous image
COPY --from=builder /var/www/laravel .
RUN chown -R www-data:www-data /var/www
EXPOSE 9000
CMD [ "php-fpm" ]