# Creating Dashboards with Grafana

## Introduction
Grafana is an open-source visualization and analytics platform used to create dashboards from metrics collected by monitoring systems such as Prometheus. This document outlines the steps required to install Grafana, connect it to Prometheus, and create dashboards to visualize metrics.

---

## Installing Grafana

Grafana can be installed on multiple operating systems. Below are the general steps for installation.

### Installation Steps
1. Download Grafana from the official Grafana website.
2. Install Grafana using the appropriate package or installer for your operating system.
3. Start the Grafana service.
4. Access the Grafana web interface.

Grafana is accessible by default at:
```

[http://localhost:3000](http://localhost:3000)

```

Default login credentials:
- Username: `admin`
- Password: `admin`

---

## Adding Prometheus as a Data Source

To visualize Prometheus metrics, Prometheus must be added as a data source in Grafana.

### Steps to Add Prometheus
1. Log in to the Grafana UI.
2. Navigate to **Configuration → Data Sources**.
3. Click **Add data source**.
4. Select **Prometheus** from the list.
5. Set the Prometheus URL to:
```

[http://localhost:9090](http://localhost:9090)

```
6. Click **Save & Test** to verify the connection.

---

## Creating Visualizations in Grafana

Grafana dashboards consist of panels that display data using different visual formats such as graphs and tables.

### Creating a New Dashboard
1. Click **Create → Dashboard**.
2. Select **Add new panel**.
3. Choose Prometheus as the data source.

---

### Example Visualizations

#### Graph Visualization
- Metric example:
```

up

```
- Displays whether monitored targets are up (1) or down (0).
- Useful for availability monitoring.

---

#### Table Visualization
- Metric example:
```

http_requests_total

```
- Displays request counts by labels such as method or status.
- Useful for viewing aggregated metrics in tabular form.

---

### Configuring Panels
- Select visualization type (Time series, Table, Bar chart).
- Configure queries using PromQL.
- Adjust time ranges and legends for clarity.

---

## Saving and Sharing Dashboards

### Saving a Dashboard
1. Click **Save dashboard**.
2. Provide a meaningful name and description.
3. Choose a folder if required.

---

### Sharing Dashboards
Grafana allows dashboards to be shared by:
- Exporting the dashboard as JSON
- Sharing dashboard links with users
- Using snapshot links for read-only access

---

## Best Practices for Dashboard Design
- Use clear and descriptive panel titles.
- Avoid overcrowding dashboards with too many panels.
- Group related metrics together.
- Use consistent time ranges and units.

---

## Conclusion
Grafana provides powerful tools for visualizing Prometheus metrics through flexible dashboards. By connecting Prometheus as a data source and creating meaningful visualizations, teams can effectively monitor system health and performance.