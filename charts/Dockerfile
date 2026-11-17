# No defaults: pass both explicitly with --build-arg (use a pinned tag or digest, not :latest)
ARG STATIC_ASSETS_IMAGE=required-pass-with-build-arg/static-assets:TAG
ARG DOCKER_BASE_IMAGE=required-pass-with-build-arg/docker-base:TAG

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
