ARG BUILD_FROM=owncloud/server:arm32v7
FROM ${BUILD_FROM}

# Copy root filesystem
COPY rootfs /
#copy test config file
#COPY options.json /data/options.json

RUN  apt-get update \
  && DEBIAN_FRONTEND=noninteractive apt-get install -y jq smbclient \
  && apt-get clean \
  && rm -rf /var/lib/apt/lists/* /tmp/* /var/tmp/* ~/.cache

ENTRYPOINT [ "/usr/bin/run.sh" ]
CMD ["/usr/bin/owncloud", "server"]

# Build arguments
ARG BUILD_ARCH
ARG BUILD_DATE
ARG BUILD_REF
ARG BUILD_VERSION
