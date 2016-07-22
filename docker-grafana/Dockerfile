FROM debian:jessie

#RUN apt-get update && \
#    apt-get -y --no-install-recommends install libfontconfig curl ca-certificates && \
#    apt-get clean && \
#    curl https://grafanarel.s3.amazonaws.com/builds/grafana_${GRAFANA_VERSION}_amd64.deb > /tmp/grafana.deb && \
#    dpkg -i /tmp/grafana.deb && \
#    rm /tmp/grafana.deb && \
#    curl -L https://github.com/tianon/gosu/releases/download/1.7/gosu-amd64 > /usr/sbin/gosu && \
#    chmod +x /usr/sbin/gosu && \
#    apt-get remove -y curl && \
#    apt-get autoremove -y && \
#    rm -rf /var/lib/apt/lists/*

RUN apt-get update && \
    apt-get -y install apt-transport-https

RUN echo "deb https://packagecloud.io/grafana/stable/debian/ wheezy main" >> /etc/apt/sources.list && \
    apt-get update && \
    apt-cache show grafana && \
    apt-get -y --no-install-recommends install grafana curl

RUN curl -L https://github.com/tianon/gosu/releases/download/1.7/gosu-amd64 > /usr/sbin/gosu && \
    chmod +x /usr/sbin/gosu && \
    apt-get remove -y curl && \
    apt-get autoremove -y && \
    rm -rf /var/lib/apt/lists/*

VOLUME ["/var/lib/grafana", "/var/lib/grafana/plugins", "/var/log/grafana", "/etc/grafana"]

EXPOSE 3000

COPY ./scripts/run.sh /run.sh

ENTRYPOINT ["/run.sh"]
