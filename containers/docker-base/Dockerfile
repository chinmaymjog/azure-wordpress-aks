FROM wordpress:7.1.5-php8.3-apache
# Pull in available OS security fixes on top of the upstream image
RUN apt-get update && apt-get upgrade -y && rm -rf /var/lib/apt/lists/*
WORKDIR /usr/src/wordpress
RUN docker-php-ext-install pdo pdo_mysql
COPY src/custom.ini $PHP_INI_DIR/conf.d/
COPY src/sample.htaccess .htaccess
RUN set -eux; \
	find /etc/apache2 -name '*.conf' -type f -exec sed -ri -e "s!/var/www/html!$PWD!g" -e "s!Directory /var/www/!Directory $PWD!g" '{}' +; \
	cp -s wp-config-docker.php wp-config.php
# Install wp-cli, pinned to a release and verified against its published sha512
ARG WP_CLI_VERSION=2.12.0
ARG WP_CLI_SHA512=be928f6b8ca1e8dfb9d2f4b75a13aa4aee0896f8a9a0a1c45cd5d2c98605e6172e6d014dda2e27f88c98befc16c040cbb2bd1bfa121510ea5cdf5f6a30fe8832
RUN set -eux; \
	curl -fsSL -o /tmp/wp-cli.phar "https://github.com/wp-cli/wp-cli/releases/download/v${WP_CLI_VERSION}/wp-cli-${WP_CLI_VERSION}.phar"; \
	echo "${WP_CLI_SHA512}  /tmp/wp-cli.phar" | sha512sum -c -; \
	php /tmp/wp-cli.phar --info; \
	chmod +x /tmp/wp-cli.phar; \
	mv /tmp/wp-cli.phar /usr/local/bin/wp
