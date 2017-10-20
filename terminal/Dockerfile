ARG BUILD_FROM=hassioaddons/base-amd64:1.0.0
FROM ${BUILD_FROM}

# Add env
ENV LANG="C.UTF-8" \
    TERM="xterm-256color"

# Copy data
COPY files/run.sh /
COPY files/hassio /usr/bin/
COPY files/motd /etc/
COPY files/.zshrc /root/
COPY files/.tmux.conf /root/

# Setup base
RUN apk add --no-cache jq openssh-client sudo zsh openssl libxml2-utils \
    ncurses curl wget net-tools bind-tools rsync git nmap wget awake \
    nano vim mosquitto-clients mariadb-client tmux ttyd && \
    git clone git://github.com/robbyrussell/oh-my-zsh.git ~/.oh-my-zsh && \
    chmod a+x /run.sh /usr/bin/hassio

CMD [ "/run.sh" ]

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
    org.label-schema.url="https://addons.community" \
    org.label-schema.usage="https://github.com/hassio-addons/addon-terminal/tree/master/README.md" \
    org.label-schema.vcs-ref=${BUILD_REF} \
    org.label-schema.vcs-url="https://github.com/hassio-addons/addon-terminal" \
    org.label-schema.vendor="Community Hass.io Add-ons"