FROM ubuntu:20.04

ENV DEBIAN_FRONTEND=noninteractive

RUN apt-get update && \
    apt-get install -y wget tar && \
    apt-get clean && \
    rm -rf /var/lib/apt/lists/*

RUN useradd --no-create-home --shell /bin/false prometheus

# Create directories
RUN mkdir -p /etc/prometheus /var/lib/prometheus

# Download and install Prometheus
WORKDIR /tmp
RUN wget https://github.com/prometheus/prometheus/releases/download/v2.48.0/prometheus-2.48.0.linux-amd64.tar.gz && \
    tar xvf prometheus-2.48.0.linux-amd64.tar.gz && \
    cp prometheus-2.48.0.linux-amd64/prometheus /usr/local/bin/ && \
    cp prometheus-2.48.0.linux-amd64/promtool /usr/local/bin/ && \
    chown prometheus:prometheus /usr/local/bin/prometheus && \
    chown prometheus:prometheus /usr/local/bin/promtool && \
    chown -R prometheus:prometheus /etc/prometheus && \
    chown -R prometheus:prometheus /var/lib/prometheus && \
    rm -rf /tmp/prometheus-*

# Copy configuration
COPY prometheus.yml /etc/prometheus/prometheus.yml
RUN chown prometheus:prometheus /etc/prometheus/prometheus.yml

USER prometheus
EXPOSE 9090

CMD ["prometheus", "--config.file=/etc/prometheus/prometheus.yml", "--storage.tsdb.path=/var/lib/prometheus/", "--web.console.templates=/etc/prometheus/consoles", "--web.console.libraries=/etc/prometheus/console_libraries"]