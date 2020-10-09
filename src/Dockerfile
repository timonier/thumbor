FROM debian:stable-slim

LABEL \
    maintainer="Morgan AUCHEDE <morgan.auchede@gmail.com>"

ENV \
    LC_ALL=C.UTF-8 \
    S6_BEHAVIOUR_IF_STAGE2_FAILS=2 \
    S6_KEEP_ENV=1 \
    S6_READ_ONLY_ROOT=1

RUN set -e -u -x \
\
    # Prepare system
\
    && export DEBIAN_FRONTEND=noninteractive \
    && apt-get update \
\
    # Install packages
\
    && BUILD_DEPS="build-essential curl gnutls-dev libcurl4-gnutls-dev python-dev python-pip" \
    && apt-get install --no-install-recommends --yes ${BUILD_DEPS} \
    && apt-get install --no-install-recommends --yes ca-certificates gnupg locales python-opencv python-setuptools \
\
    # Install dockerize
\
    && curl --location "https://github.com/jwilder/dockerize/releases/download/v0.6.1/dockerize-linux-amd64-v0.6.1.tar.gz" | tar --directory /usr/local/bin --extract --gzip \
    && chmod +x /usr/local/bin/dockerize \
\
    # Install s6-overlay
\
    && curl "https://keybase.io/justcontainers/key.asc" | gpg --import \
    && curl --location --output /tmp/s6-overlay.tar.gz "https://github.com/just-containers/s6-overlay/releases/download/v2.1.0.0/s6-overlay-amd64.tar.gz" \
    && curl --location --output /tmp/s6-overlay.tar.gz.sig "https://github.com/just-containers/s6-overlay/releases/download/v2.1.0.0/s6-overlay-amd64.tar.gz.sig" \
    && gpg --verify /tmp/s6-overlay.tar.gz.sig /tmp/s6-overlay.tar.gz \
    && tar --directory / --extract --file /tmp/s6-overlay.tar.gz --gzip \
\
    # Install thumbor
\
    && pip install thumbor \
\
    # Clean
\
    && apt-get remove --purge --yes ${BUILD_DEPS} \
    && apt-get autoremove --purge --yes \
    && rm -f -r /root/.gnupg /tmp/* /var/lib/apt/lists/*

COPY rootfs/ /

ENTRYPOINT [ "/init" ]
