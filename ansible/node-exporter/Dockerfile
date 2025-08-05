FROM ubuntu:20.04

ENV DEBIAN_FRONTEND=noninteractive

RUN apt-get update && \
    apt-get install -y wget tar && \
    apt-get clean && \
    rm -rf /var/lib/apt/lists/*

RUN useradd --no-create-home --shell /bin/false node_exporter

WORKDIR /tmp
RUN wget https://github.com/prometheus/node_exporter/releases/download/v1.8.0/node_exporter-1.8.0.linux-amd64.tar.gz && \
    tar xvf node_exporter-1.8.0.linux-amd64.tar.gz && \
    cp node_exporter-1.8.0.linux-amd64/node_exporter /usr/local/bin/ && \
    chown node_exporter:node_exporter /usr/local/bin/node_exporter && \
    rm -rf /tmp/node_exporter-*

USER node_exporter
EXPOSE 9100

CMD ["node_exporter"]