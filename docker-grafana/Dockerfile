FROM debian:jessie

RUN apt-get update && \
    apt-get -y install apt-transport-https curl

RUN echo "deb https://packagecloud.io/grafana/stable/debian/ wheezy main" >> /etc/apt/sources.list && \
    curl https://packagecloud.io/gpg.key | sudo apt-key add - && \
    apt-get update && \
    apt-get -y --no-install-recommends install grafana

RUN curl -L https://github.com/tianon/gosu/releases/download/1.7/gosu-amd64 > /usr/sbin/gosu && \
    chmod +x /usr/sbin/gosu && \
    apt-get remove -y curl && \
    apt-get autoremove -y && \
    rm -rf /var/lib/apt/lists/*

VOLUME ["/var/lib/grafana", "/var/lib/grafana/plugins", "/var/log/grafana", "/etc/grafana"]

EXPOSE 3000

COPY ./scripts/run.sh /run.sh

ENTRYPOINT ["/run.sh"]
