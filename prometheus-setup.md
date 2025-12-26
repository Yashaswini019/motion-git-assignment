# Setting Up Basic Monitoring with Prometheus

## Introduction
Prometheus is an open-source monitoring system that collects metrics from configured targets and stores them as time-series data. This document outlines the steps required to set up basic monitoring with Prometheus, including installation, configuration, and metric scraping.

---

## Installing the Prometheus Server

Prometheus can be installed on Linux, macOS, or Windows. Below are the general installation steps.

### Installation Steps
1. Download the Prometheus binary from the official Prometheus website.
2. Extract the downloaded archive.
3. Navigate to the extracted directory.
4. Start the Prometheus server using the executable.

Example command:
```bash
./prometheus --config.file=prometheus.yml
````

Once started, the Prometheus web interface can be accessed at:

```
http://localhost:9090
```

---

## Configuring Prometheus to Scrape Metrics

Prometheus uses a configuration file (`prometheus.yml`) to define:

* Which targets to monitor
* How often metrics should be scraped

Metrics are typically exposed by applications or services via an HTTP endpoint such as `/metrics`.

---

## Example Prometheus Configuration File

Below is a sample `prometheus.yml` configuration for scraping metrics from Prometheus itself or a sample application.

```yaml
global:
  scrape_interval: 15s
  evaluation_interval: 15s

scrape_configs:
  - job_name: "prometheus"
    static_configs:
      - targets: ["localhost:9090"]
```

---

## Explanation of Key Configuration Settings

### Global Settings

* **scrape_interval**: Defines how often Prometheus scrapes metrics from targets.
* **evaluation_interval**: Defines how often Prometheus evaluates alert rules.

---

### Scrape Configurations

* **job_name**: A logical name for the monitored service.
* **static_configs**: Defines static targets to scrape.
* **targets**: List of hostnames and ports where metrics are exposed.

---

## Verifying Metric Collection

After starting Prometheus:

1. Open the Prometheus UI.
2. Navigate to the **Status → Targets** page.
3. Ensure the configured targets are marked as **UP**.
4. Use the query interface to explore available metrics.

---

## Conclusion

By installing Prometheus and configuring it with a simple `prometheus.yml` file, basic monitoring can be set up quickly. Prometheus can scrape metrics from applications, system exporters, or other services and store them for querying and visualization.