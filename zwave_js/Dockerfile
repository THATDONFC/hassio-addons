ARG BUILD_FROM
FROM ${BUILD_FROM}

ARG ZWAVEJS_SERVER_VERSION
ARG ZWAVEJS_VERSION

# Install Z-Wave JS
WORKDIR /usr/src
RUN \
    set -x \
    && apk add --no-cache \
        nodejs \
        npm \
    && apk add --no-cache --virtual .build-dependencies \
        build-base \
        git \
        linux-headers \
        python3 \
    \
    && npm config set unsafe-perm \
    && npm install \
        "zwave-js@${ZWAVEJS_VERSION}" \
        "@zwave-js/core@${ZWAVEJS_CORE_VERSION}" \
        "@zwave-js/serial@${ZWAVEJS_SERIAL_VERSION}" \
        "@zwave-js/config@${ZWAVEJS_CONFIG_VERSION}" \
        "@zwave-js/shared@${ZWAVEJS_SHARED_VERSION}" \
        "@zwave-js/server@${ZWAVEJS_SERVER_VERSION}" \
    \
    && apk del --no-cache \
        .build-dependencies

WORKDIR /
COPY rootfs /

ENV PATH=/usr/src/node_modules/.bin:$PATH
