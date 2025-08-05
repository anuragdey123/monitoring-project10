FROM ubuntu:20.04

ENV DEBIAN_FRONTEND=noninteractive

RUN apt-get update && \
    apt-get install -y wget adduser libfontconfig1 musl && \
    wget https://dl.grafana.com/oss/release/grafana_10.3.1_amd64.deb && \
    dpkg -i grafana_10.3.1_amd64.deb && \
    apt-get clean && \
    rm -rf /var/lib/apt/lists/* && \
    rm grafana_10.3.1_amd64.deb

EXPOSE 3000

CMD ["/usr/sbin/grafana-server", "--homepath=/usr/share/grafana", "--config=/etc/grafana/grafana.ini"]