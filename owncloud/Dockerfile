ARG OWNCLOUD_VERSION=10.5.0
FROM owncloud/server:${OWNCLOUD_VERSION}

# Copy root filesystem
COPY rootfs /
#copy test config file
#COPY options.json /data/options.json

RUN  apt-get update \
  && DEBIAN_FRONTEND=noninteractive apt-get install -y jq smbclient \
  && apt-get clean \
  && rm -rf /var/lib/apt/lists/* /tmp/* /var/tmp/* ~/.cache

# Change the root folder for Nextcloud to the /share directory to be persistent
RUN  #sed -i "s|/var/www|/share/owncloud|g" /etc/apache2/sites-enabled/000-default.conf \
  && sed -i "s|/var/www|/share/owncloud|g" /etc/apache2/apache2.conf \
  && sed -i "s|/var/www/html|/share/owncloud/html|g" /entrypoint.sh \
  && sed -i "s|/var/www/html|/share/owncloud/html|g" /usr/src/owncloud/config/autoconfig.php
  
# RUN echo "ServerName localhost" | tee /etc/apache2/conf-available/fqdn.conf && a2enconf fqdn

ENTRYPOINT [ "/usr/bin/run.sh" ]
CMD ["apache2-foreground"]

# Build arguments
ARG BUILD_ARCH
ARG BUILD_DATE
ARG BUILD_REF
ARG BUILD_VERSION
