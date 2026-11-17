# Grafana + Loki + Promtail

Log monitoring setup using Docker.

## Run Loki
docker run -d --name loki -v ~/grafana_config:/mnt/config -p 3100:3100 grafana/loki:2.8.0 -config.file=/mnt/config/loki-config.yaml

## Run Promtail
docker run -d --name promtail -v ~/grafana_config:/mnt/config -v /var/log:/var/log --link loki grafana/promtail:2.8.0 -config.file=/mnt/config/promtail-config.yaml

## Grafana
Add a Loki data source with URL http://localhost:3100
