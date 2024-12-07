ARG BUILD_FROM
FROM ${BUILD_FROM}

ARG PAPERMC_VERSION="1.20.4"
ARG PAPERMC_BUILD="361"
ARG JAVA_VERSION="openjdk-8-jre-headless"

# Set shell
SHELL ["/bin/bash", "-o", "pipefail", "-c"]

RUN \
    apt-get -y update -y \
    && apt-get -y install yq \
    && apt-get -y install unzip \
    && apt-get -y install $JAVA_VERSION

# Copy root filesystem
COPY rootfs /

# Copy defualt Configs
RUN mkdir /default_config
COPY default_config/* /default_config/

# Corrects permissions for s6 v3
RUN if [ -d /etc/services.d ]; then chmod -R 755 /etc/services.d; fi && \
    if [ -d /etc/services.d/ha-spawn-point-the1710pack ]; then chmod -R 755 /etc/services.d/ha-spawn-point-the1710pack; fi

# get server files 
RUN mkdir -p /opt/minecraft
# Download server files
#https://solder.endermedia.com/repository/downloads/the-1710-pack/the-1710-pack_0.10.15.zip
RUN curl --no-progress-meter -H "Accept-Encoding: identity" -H "Accept-Language: en" -L -A "Mozilla/5.0 (Windows NT 10.0; Win64; x64) AppleWebKit/537.36 (KHTML, like Gecko) Chrome/" -o /tmp/the-1710-pack_0.10.15.zip "https://solder.endermedia.com/repository/downloads/the-1710-pack/the-1710-pack_0.10.15.zip"
# Extract server files
RUN unzip /tmp/the-1710-pack_0.10.15.zip -d /opt/minecraft
# Remove zip file
RUN rm /tmp/the-1710-pack_0.10.15.zip
# Copy server.properties
RUN cp /default_config/server.properties /minecraft/server.properties
# Copy eula.txt
RUN cp /default_config/eula.txt /minecraft/eula.txt

############
# 5 Labels #
############

ARG BUILD_ARCH
ARG BUILD_DATE
ARG BUILD_DESCRIPTION
ARG BUILD_NAME
ARG BUILD_REF
ARG BUILD_REPOSITORY
ARG BUILD_VERSION
LABEL \
    io.hass.name="${BUILD_NAME}" \
    io.hass.description="${BUILD_DESCRIPTION}" \
    io.hass.arch="${BUILD_ARCH}" \
    io.hass.type="addon" \
    io.hass.version=${BUILD_VERSION} \
    maintainer="rvpettigrew (https://github.com/rvpettigrew)" \
    org.opencontainers.image.title="${BUILD_NAME}" \
    org.opencontainers.image.description="${BUILD_DESCRIPTION}" \
    org.opencontainers.image.vendor="Home Assistant Add-ons" \
    org.opencontainers.image.authors="rvpettigrew (https://github.com/rvpettigrew)" \
    org.opencontainers.image.licenses="Apache" \
    org.opencontainers.image.url="https://github.com/rvpettigrew" \
    org.opencontainers.image.source="https://github.com/${BUILD_REPOSITORY}" \
    org.opencontainers.image.documentation="https://github.com/${BUILD_REPOSITORY}/blob/main/README.md" \
    org.opencontainers.image.created=${BUILD_DATE} \
    org.opencontainers.image.revision=${BUILD_REF} \
    org.opencontainers.image.version=${BUILD_VERSION}
