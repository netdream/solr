FROM solr:6.3-alpine
MAINTAINER Wodby <hello@wodby.com>

ENV SOLR_HEAP 1024m

USER 0
RUN apk add --no-cache sudo curl \
    && echo 'solr ALL=(root) NOPASSWD: /opt/docker-solr/scripts/solr-fix-permissions' > /etc/sudoers.d/solr
USER $SOLR_USER

RUN cp -r /opt/solr/server/solr/solr.xml /opt/docker-solr/solr.xml \
    && cp -r /opt/solr/server/solr/configsets /opt/docker-solr/configsets

COPY scripts /opt/docker-solr/scripts
COPY docker-entrypoint-initdb.d /docker-entrypoint-initdb.d

VOLUME /opt/solr/server/solr
WORKDIR /opt/solr/server/solr
