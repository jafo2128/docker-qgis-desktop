FROM qgis/qgis3-build-deps:latest
MAINTAINER Xavi Torelló <info@xaviertorello.cat>
# Based off work by Tim Sutton <tim@kartoza.com>
# Based off work by Patrick Valsecchi<patrick.valsecchi@camptocamp.com>

ENV LANG C

COPY build /build/scripts
RUN /build/scripts/getCode.sh && \
    /build/scripts/make.sh 
    /build/scripts/clean.sh

# A few tunable variables for QGIS
ENV QGIS_DEBUG 5
ENV QGIS_LOG_FILE /proc/self/fd/1
ENV PGSERVICEFILE /project/pg_service.conf
ENV QGIS_PROJECT_FILE /project/project.qgs

ADD start.sh /start.sh
RUN chmod +x /start.sh
CMD ["/start.sh"]