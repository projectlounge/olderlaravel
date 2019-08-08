### Simple docker file for older laraval projects

Use
```
FROM projectlounge/oldlaravel

#set our application folder as an environment variable
ENV APP_HOME /var/www/html

ENV COMPOSER_ALLOW_SUPERUSER=1
ENV COMPOSER_NO_INTERACTION=1

#copy source files and run composer
COPY . $APP_HOME

WORKDIR $APP_HOME

# install all PHP dependencies
RUN composer install --no-interaction

RUN service apache2 start

CMD php artisan serve --env=local --host=0.0.0.0
```
