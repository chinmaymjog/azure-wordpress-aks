ARG STATIC_ASSETS_IMAGE=ghcr.io/chinmaymjog/azure-wordpress-aks/static-assets:latest
ARG DOCKER_BASE_IMAGE=ghcr.io/chinmaymjog/azure-wordpress-aks/docker-base:latest

FROM ${STATIC_ASSETS_IMAGE} AS common

COPY /pkg-mgr/ /pkg-mgr/

RUN bash /pkg-mgr/copy_plugins_themes -t themes
RUN bash /pkg-mgr/copy_plugins_themes -t plugins

FROM ${DOCKER_BASE_IMAGE}

COPY --from=common --chown=www-data:www-data /common-themes ./wp-content/themes/
COPY --from=common --chown=www-data:www-data /common-plugins ./wp-content/plugins/

COPY src/wp-content/themes/ ./wp-content/themes/
COPY src/wp-content/plugins/ ./wp-content/plugins/
# COPY ./src/wp-config.php ./wp-config.php
