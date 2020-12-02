ARG OWNCLOUD_VERSION=10.5.0
FROM owncloud/server:${OWNCLOUD_VERSION}

# Copy root filesystem
COPY rootfs /

RUN echo "ServerName localhost" | tee /etc/apache2/conf-available/fqdn.conf && a2enconf fqdn

ENTRYPOINT [ "/usr/bin/run.sh" ]
CMD ["apache2-foreground"]

# Build arguments
ARG BUILD_ARCH
ARG BUILD_DATE
ARG BUILD_REF
ARG BUILD_VERSION
