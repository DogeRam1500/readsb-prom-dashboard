# readsb-prom-dashboard
This is a Grafana dashboard based on https://grafana.com/grafana/dashboards/18398-readsb/, but with added panels for Dump978 data.

Don't forget to edit your dump978 docker-compose.yaml to include:
```yaml
    environment:
      - PROMETHEUS_ENABLE=true
    ports:
      - 9273:9273
```

Also don't forget to run (CHANGE ip_of_dump978_machine)
```bash
docker exec -it prometheus sh -c "echo -e \"  - job_name: 'dump978'\n    static_configs:\n      - targets: ['ip_of_dump978_machine:9273']\" >> /etc/prometheus/prometheus.yml"
docker stop prometheus
docker compose up -d
```
If you screw it up, run `sudo nano /opt/grafana//prometheus/config/prometheus.yml` to edit the file
