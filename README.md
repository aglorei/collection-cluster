# InfluxDB and Grafana Cluster

This repository configures an InfluxDB server for recording metrics and a Grafana server as the web frontend for dashboard visualizations.

- [InfluxDB 1.2.2](https://hub.docker.com/_/influxdb/)
  - The image exposes a shared volume under /var/lib/influxdb, which is mounted as a Docker volume called `influxdb-volume` for peristent container data
  - Binds external port 8086 for communication over the HTTP API
- [Grafana 4.2.0](https://hub.docker.com/r/grafana/grafana/)
  - The image exposes a shared volume under /var/lib/grafana, which is mounted as a Docker volume called `grafana-volume` for peristent container data
  - Binds external port 8086 for communication over the HTTP API

#### Requirements
- Syslog server for logging

#### Quick Start:
Configure environment variables, or a `.env`:

| Variable | Description |
| ------------- | ------------- |
| `GF_SERVER_DOMAIN` | Full URL used to access Grafana from a web browser when proxied (e.g., `foobar` with https://foobar.com/grafana) |
| `SYSLOG_ADDRESS` | Syslog host, transport protocol, and port (e.g., `tcp://10.0.0.2:514`) |

To build and start containers:

```
docker-compose up -d
```

