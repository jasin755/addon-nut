ARG BUILD_FROM=ghcr.io/hassio-addons/debian-base:9.1.0
# hadolint ignore=DL3006
FROM ${BUILD_FROM}

# Setup base
# hadolint ignore=DL3003
RUN \
    echo "deb http://deb.debian.org/debian unstable main" > /etc/apt/sources.list.d/unstable.list \
    && apt-get update \
    && apt-get install -t unstable -y --no-install-recommends \
        nut \
        nut-snmp \
        nut-xml \
        nut-modbus \
        usbutils \
    && apt-get clean \
    && rm -rf /var/lib/apt/lists/*

# Copy root filesystem
COPY rootfs /

# Build arguments
ARG BUILD_ARCH
ARG BUILD_DATE
ARG BUILD_DESCRIPTION
ARG BUILD_NAME
ARG BUILD_REF
ARG BUILD_REPOSITORY
ARG BUILD_VERSION

# Labels
LABEL \
    io.hass.name="${BUILD_NAME} (Custom EcoFlow Fork)" \
    io.hass.description="${BUILD_DESCRIPTION}" \
    io.hass.arch="${BUILD_ARCH}" \
    io.hass.type="addon" \
    io.hass.version=${BUILD_VERSION} \
    maintainer="Tvoje Jmeno" \
    org.opencontainers.image.title="${BUILD_NAME}" \
    org.opencontainers.image.description="${BUILD_DESCRIPTION}" \
    org.opencontainers.image.vendor="Home Assistant Community Add-ons" \
    org.opencontainers.image.licenses="MIT"
