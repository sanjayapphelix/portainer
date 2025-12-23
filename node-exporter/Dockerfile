# Use a lightweight base image
FROM debian:bullseye-slim

# Set environment variables
ENV NODE_EXPORTER_VERSION="1.10.2"
ENV DEBIAN_FRONTEND=noninteractive

# Install dependencies required for Node Exporter binary
RUN apt-get update && \
    apt-get install -y wget ca-certificates && \
    rm -rf /var/lib/apt/lists/*

# Download Node Exporter binary (Linux AMD64!)
RUN wget https://github.com/prometheus/node_exporter/releases/download/v${NODE_EXPORTER_VERSION}/node_exporter-${NODE_EXPORTER_VERSION}.linux-amd64.tar.gz && \
    tar xvf node_exporter-${NODE_EXPORTER_VERSION}.linux-amd64.tar.gz && \
    mv node_exporter-${NODE_EXPORTER_VERSION}.linux-amd64/node_exporter /usr/local/bin/ && \
    rm -rf node_exporter-${NODE_EXPORTER_VERSION}.linux-amd64* 

# Expose the default Node Exporter port
EXPOSE 9100

# Run Node Exporter
ENTRYPOINT ["/usr/local/bin/node_exporter"]

