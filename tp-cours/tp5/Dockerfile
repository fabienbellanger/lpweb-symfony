FROM php:7.4-apache

RUN apt-get update

# Git
# ---
RUN apt-get install -y git unzip zip

# wget
# ----
RUN apt-get install -y wget
RUN wget https://get.symfony.com/cli/installer -O - | bash
RUN mv /root/.symfony/bin/symfony /usr/local/bin/symfony

# Composer
# --------
RUN curl -sS https://getcomposer.org/installer | php \
	&& mv composer.phar /usr/local/bin/ \
	&& ln -s /usr/local/bin/composer.phar /usr/local/bin/composer

# Extensions PHP
# --------------
RUN docker-php-ext-install pdo pdo_mysql

# Xdebug
# ------
RUN pecl install xdebug && docker-php-ext-enable xdebug

WORKDIR /app
COPY . /app

# Lancement du serveur local
# --------------------------
CMD [ "symfony", "server:start", "--port=8000", "--no-tls" ]
