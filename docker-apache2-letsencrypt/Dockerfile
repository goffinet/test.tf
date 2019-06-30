FROM enoniccloud/apache2

LABEL creator="Erik Kaareng-Sunde <https://github.com/drerik>"

RUN rm /etc/apache2/sites-enabled/000-default.conf \
  && rm /etc/apache2/sites-enabled/default-ssl.conf \
  && apt-get update && apt-get -y install curl && apt-get clean \
  && curl -o /usr/local/bin/certbot-auto https://dl.eff.org/certbot-auto && \
  chmod +x /usr/local/bin/certbot-auto && \
  certbot-auto --os-packages-only -n

COPY 0-default.conf /etc/apache2/sites-enabled/0-default.conf
COPY html/index.html /var/www/html/index.html
COPY html/test /var/www/html/test
COPY html/status /var/www/html/status
COPY launcher.sh /usr/local/bin/launcher.sh
RUN chmod +x /usr/local/bin/launcher.sh
RUN a2enmod headers
CMD /usr/local/bin/launcher.sh
