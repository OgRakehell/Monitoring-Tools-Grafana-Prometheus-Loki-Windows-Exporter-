# Configurations

## Introduction
After installation, configuration ensures each component (Prometheus, Loki, Promtail, Grafana) communicates properly.  
This section walks through the essential configuration steps.

---

## Configuration Files Overview
- **Prometheus** → `prometheus.yml`  
- **Loki** → `loki-config.yaml`  
- **Promtail** → `promtail-config.yaml`  
- **Grafana** → `grafana.ini`  

---

## Prometheus Configuration
### File: `prometheus.yml`
- Define scrape targets (exporters, servers, etc.).
- Example:
```yaml
scrape_configs:
  - job_name: "windows"
    static_configs:
      - targets: ["localhost:9182"]
````
---

## Loki Configuration
### File: `loki-config.yaml`

Set ports, storage, retention.

**Example:**
```yaml
server:
  http_listen_port: 3100
ingester:
  lifecycler:
    ring:
      kvstore:
        store: inmemory
```
---
## Promtail Configuration
### File: `promtail-config.yaml`

Point to logs, add labels, and push to Loki.

**Example:**
```yaml
server:
  http_listen_port: 9080
positions:
  filename: /tmp/positions.yaml
clients:
  - url: http://localhost:3100/loki/api/v1/push
```
---
## Grafana Configuration
### File: `grafana.ini`

- Change admin credentials.  
- Configure data sources (Loki, Prometheus).

### Steps:

1. Log into Grafana at [http://localhost:3000](http://localhost:3000)  
2. Go to **Home > Connections > Data Sources**  
3. Add **Prometheus** and **Loki**

---
## Verification

Check that each component of your monitoring stack is running correctly:

### Prometheus
- Access your scrape targets: [http://localhost:9090/targets](http://localhost:9090/targets)  
- Expected: Your Windows Exporter (or other targets) should appear as `UP`.  

![Prometheus Targets](assets/prometheus.png)

---

### Loki
- Access Loki metrics: [http://localhost:3100/metrics](http://localhost:3100/metrics)  
- Expected: Metrics should be displayed, confirming Loki is running.  

![Loki Metrics](assets/loki-metrics.png)

---

### Grafana
- Access Grafana dashboard: [http://localhost:3000](http://localhost:3000)  
- Expected: Log in and confirm that data sources (Prometheus, Loki) are available.  

![Grafana Dashboard](assets/grafana.png)


