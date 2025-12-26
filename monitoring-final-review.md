# Monitoring in DevOps: Final Review

This document consolidates all monitoring-related topics in DevOps, including the importance of monitoring, key metrics and KPIs, popular tools, and implementation using Prometheus and Grafana.

---

## 1. Importance of Monitoring

Monitoring is a critical component of the DevOps lifecycle. It ensures that systems are operating efficiently and reliably while helping teams respond quickly to issues. Key benefits include:

- **Performance Management**: Continuous monitoring helps detect bottlenecks in CPU, memory, storage, and network usage, enabling optimization.  
- **Reliability & Uptime**: Monitoring ensures applications and services remain available, minimizing downtime.  
- **User Satisfaction**: By maintaining performance and availability, user experience is improved.  
- **Proactive Issue Detection**: Identify potential problems before they impact end-users.  
- **Capacity Planning**: Track resource usage trends to plan for scaling infrastructure.  

---

## 2. Key Metrics and KPIs

Effective monitoring relies on metrics that provide insights into system performance, availability, and user experience. Common categories:

### 2.1 System Metrics
- CPU usage
- Memory utilization
- Disk I/O and storage capacity
- Network throughput and latency

### 2.2 Application Metrics
- Request rate, error rate, and response time
- Database query performance
- Background job/queue status

### 2.3 Business Metrics
- Transactions per second or user actions
- Key performance indicators (KPIs) specific to business goals
- User engagement metrics  

Monitoring these metrics ensures teams can maintain optimal system performance and meet SLA requirements.

---

## 3. Overview of Monitoring Tools

### 3.1 Prometheus
- **Features**: Time-series database, PromQL query language, multi-dimensional data model.  
- **Architecture**: Pull-based metric collection from endpoints, supports alerting rules.  
- **Use Cases**: Containerized applications, microservices, infrastructure monitoring.

### 3.2 Grafana
- **Features**: Dashboarding and visualization tool, supports multiple data sources.  
- **Integration**: Connects with Prometheus, InfluxDB, Elasticsearch, and others.  
- **Use Cases**: Visualizing metrics, alert dashboards, reporting trends.

### 3.3 Nagios
- **Features**: Monitoring network, servers, and applications with alerting capabilities.  
- **Strengths**: Stable, widely adopted, plugin ecosystem.  
- **Use Cases**: Traditional infrastructure monitoring, alerting on server/service failures.

---

## 4. Tools Implementation: Prometheus & Grafana

### 4.1 Installing Prometheus

```bash
wget https://github.com/prometheus/prometheus/releases/download/v2.48.0/prometheus-2.48.0.linux-amd64.tar.gz
tar xvf prometheus-2.48.0.linux-amd64.tar.gz
cd prometheus-2.48.0.linux-amd64
./prometheus --config.file=prometheus.yml
````

**prometheus.yml example:**

```yaml
global:
  scrape_interval: 15s

scrape_configs:
  - job_name: 'sample-app'
    static_configs:
      - targets: ['localhost:8080']
```

---

### 4.2 Installing Grafana

```bash
sudo apt-get install -y software-properties-common
sudo add-apt-repository "deb https://packages.grafana.com/oss/deb stable main"
sudo apt-get update
sudo apt-get install grafana
sudo systemctl start grafana-server
sudo systemctl enable grafana-server
```

* Open Grafana at `http://localhost:3000` (default login: admin/admin).
* Add Prometheus as a data source (**Configuration > Data Sources > Add Data Source > Prometheus**) → URL: `http://localhost:9090`.

---

### 4.3 Monitoring a Sample Application

**Node.js example exposing metrics:**

```javascript
const express = require('express');
const client = require('prom-client');

const app = express();
const collectDefaultMetrics = client.collectDefaultMetrics;
collectDefaultMetrics();

app.get('/metrics', (req, res) => {
  res.set('Content-Type', client.register.contentType);
  res.end(client.register.metrics());
});

app.get('/', (req, res) => res.send('Hello World!'));
app.listen(8080, () => console.log('App running on port 8080'));
```

* Prometheus scrapes metrics from `http://localhost:8080/metrics`.
* Grafana dashboards can visualize CPU usage, memory usage, and request counts.

---

### 4.4 Example Grafana Dashboard Panels

* **CPU Usage**: `node_cpu_seconds_total`
* **Memory Usage**: `node_memory_Active_bytes`
* **Request Count**: `http_requests_total`
