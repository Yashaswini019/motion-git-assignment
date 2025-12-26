# Prometheus Architecture and Data Model

## Introduction
Prometheus is an open-source monitoring and alerting system designed for reliability and scalability. It is widely used in cloud-native and microservices-based environments to collect, store, and query metrics in real time.

This document explains the **architecture of Prometheus**, its **key components**, and its **data model**.

---

## Prometheus Architecture Overview

Prometheus follows a **pull-based architecture**, where it actively scrapes metrics from configured targets at regular intervals.

### High-Level Architecture Flow
1. Applications and systems expose metrics.
2. Prometheus server scrapes these metrics.
3. Metrics are stored as time-series data.
4. PromQL is used to query metrics.
5. Alerts are generated and sent to Alertmanager.
6. Visualization tools (e.g., Grafana) display metrics.

---

## Key Components of Prometheus

### 1. Prometheus Server
The Prometheus server is the core component responsible for:
- Scraping metrics from configured targets
- Storing metrics in a time-series database
- Evaluating alert rules
- Providing a query interface using PromQL

It consists of:
- **Retrieval**: Scrapes metrics from endpoints
- **Storage**: Stores time-series data locally
- **Query Engine**: Executes PromQL queries

---

### 2. Data Storage
Prometheus stores data locally on disk in a **custom time-series database (TSDB)**.

Key characteristics:
- Efficient storage for time-series data
- Data is stored with timestamps
- Retention policies control how long data is kept
- Not designed for long-term archival by default

---

### 3. Exporters
Exporters are components that expose metrics from systems that do not natively support Prometheus.

Common exporters include:
- **Node Exporter** – system-level metrics (CPU, memory, disk)
- **MySQL Exporter** – database metrics
- **JVM Exporter** – Java application metrics

Exporters expose metrics over HTTP, usually at:
```

/metrics

````

---

### 4. Pushgateway
The Pushgateway is used for:
- Short-lived or batch jobs
- Jobs that cannot be scraped reliably

Instead of being scraped, metrics are **pushed** to the Pushgateway, and Prometheus scrapes the Pushgateway.

---

### 5. Alertmanager
Alertmanager handles alerts sent by Prometheus.

Responsibilities:
- Deduplication of alerts
- Grouping related alerts
- Routing alerts to notification channels (Email, Slack, PagerDuty, etc.)

---

### 6. Visualization Tools (Grafana)
Prometheus does not focus on visualization. Tools like **Grafana** are commonly used to:
- Create dashboards
- Visualize metrics in graphs and tables
- Share monitoring insights with teams

---

## Prometheus Data Model

Prometheus uses a **multi-dimensional data model** based on time series.

### Time Series
A time series is identified by:
- A **metric name**
- A set of **labels**
- A timestamped value

Example:
```text
http_requests_total{method="GET", status="200"} 1024
````

---

### Metric Names

Metric names describe what is being measured and should be:

* Clear
* Descriptive
* Written in snake_case

Example:

```
cpu_usage_seconds_total
```

---

### Labels

Labels provide additional dimensions to metrics.

Example labels:

* `instance`
* `job`
* `method`
* `status`

Labels allow powerful filtering and aggregation.

---

## Metric Types

### 1. Counter

* Represents a monotonically increasing value
* Used for counts (e.g., requests served)
* Can only increase or reset to zero

Example:

```
http_requests_total
```

---

### 2. Gauge

* Represents a value that can go up or down
* Used for current states

Examples:

* CPU usage
* Memory usage
* Number of active connections

---

### 3. Histogram

* Samples observations into configurable buckets
* Used for request durations or response sizes

Provides:

* Count
* Sum
* Buckets

---

### 4. Summary

* Similar to histograms but calculated on the client side
* Provides quantiles (e.g., 95th percentile)
* More expensive in terms of performance

---

## Conclusion

Prometheus provides a robust and scalable monitoring solution using a pull-based architecture and a flexible time-series data model. Its modular design, combined with exporters and visualization tools like Grafana, makes it suitable for modern distributed systems.