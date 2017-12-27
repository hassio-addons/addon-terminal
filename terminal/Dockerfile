ARG BUILD_FROM=hassioaddons/base-amd64:1.3.0
FROM ${BUILD_FROM}

# Add env
ENV LANG="C.UTF-8" \
    TERM="xterm-256color"

# Setup base
RUN \
    apk add --no-cache \
        awake \
        bind-tools \
        git \
        libxml2-utils \
        mariadb-client \
        mosquitto-clients \
        nano \
        ncurses \
        net-tools \
        nmap \
        openssh-client \
        openssl \
        rsync \
        sudo \
        tmux \
        ttyd \
        vim \
        wget \
        zsh \
    \
    && git clone git://github.com/robbyrussell/oh-my-zsh.git ~/.oh-my-zsh

# Copy root filesystem
COPY rootfs /

# Build arugments
ARG BUILD_ARCH
ARG BUILD_DATE
ARG BUILD_REF
ARG BUILD_VERSION

# Labels
LABEL \
    io.hass.name="Terminal" \
    io.hass.description="Terminal access to your Home Assistant instance via the web" \
    io.hass.arch="${BUILD_ARCH}" \
    io.hass.type="addon" \
    io.hass.version=${BUILD_VERSION} \
    maintainer="Franck Nijhof <frenck@addons.community>" \
    org.label-schema.description="Terminal access to your Home Assistant instance via the web" \
    org.label-schema.build-date=${BUILD_DATE} \
    org.label-schema.name="Terminal" \
    org.label-schema.schema-version="1.0" \
    org.label-schema.url="https://community.home-assistant.io/t/community-hass-io-add-on-terminal/33814?u=frenck" \
    org.label-schema.usage="https://github.com/hassio-addons/addon-terminal/tree/master/README.md" \
    org.label-schema.vcs-ref=${BUILD_REF} \
    org.label-schema.vcs-url="https://github.com/hassio-addons/addon-terminal" \
    org.label-schema.vendor="Community Hass.io Add-ons"
