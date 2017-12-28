FROM debian:jessie

MAINTAINER Johnson Xu <itjohnsonxu@gmail.com>

ENV FILEBEAT_VERSION=6.1.1 \
    FILEBEAT_HOME=/opt/filebeat
WORKDIR ${FILEBEAT_HOME}

RUN set -x && \
  apt-get update && \
  apt-get install -y wget && \
  wget https://artifacts.elastic.co/downloads/beats/filebeat/filebeat-${FILEBEAT_VERSION}-linux-x86_64.tar.gz -O /opt/filebeat.tar.gz && \
  cd /opt && \
  tar xzf filebeat.tar.gz && \
  rm -fr /opt/filebeat.tar.gz && \
  ln -sv filebeat-${FILEBEAT_VERSION}-linux-x86_64/ /opt/filebeat && \
  rm -fr filebeat/filebeat.yml && \
  apt-get purge -y wget && \
  apt-get autoremove -y && \
  apt-get clean && rm -rf /var/lib/apt/lists/* /tmp/* /var/tmp/*

CMD [ "./filebeat", "-e" ]
