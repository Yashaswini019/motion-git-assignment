
---

## Installing and Configuring Kibana for Log Visualization

### Prerequisites

* Elasticsearch installed and running
* Linux system (Ubuntu 20.04+ recommended)
* Access to Elasticsearch endpoint (default: `http://localhost:9200`)
* Open port: **5601**

---

## 1. Installation Instructions

### Option A: Install Kibana on Ubuntu (APT – Recommended)

1. **Add Elastic GPG key**

```bash
curl -fsSL https://artifacts.elastic.co/GPG-KEY-elasticsearch | sudo apt-key add -
```

2. **Add Elastic repository**

```bash
echo "deb https://artifacts.elastic.co/packages/8.x/apt stable main" | \
sudo tee /etc/apt/sources.list.d/elastic-8.x.list
```

3. **Update package index and install Kibana**

```bash
sudo apt update
sudo apt install kibana
```

4. **Enable and start Kibana**

```bash
sudo systemctl enable kibana
sudo systemctl start kibana
```

---

### Option B: Install Using Docker (Optional)

```bash
docker run -d --name kibana \
-p 5601:5601 \
-e ELASTICSEARCH_HOSTS=http://host.docker.internal:9200 \
docker.elastic.co/kibana/kibana:8.x
```

---

## 2. Configuration Settings (`kibana.yml`)

The main configuration file is located at:

```bash
/etc/kibana/kibana.yml
```

### Basic Configuration

```yaml
server.port: 5601
server.host: "0.0.0.0"

elasticsearch.hosts: ["http://localhost:9200"]

kibana.index: ".kibana"

logging.dest: /var/log/kibana/kibana.log
```

### Configuration Notes

* `server.host`: Set to `0.0.0.0` to allow external access
* `elasticsearch.hosts`: Points Kibana to Elasticsearch
* `logging.dest`: Stores Kibana logs locally

After changes, restart Kibana:

```bash
sudo systemctl restart kibana
```

---

## 3. Connecting Kibana to Elasticsearch

### Step 1: Access Kibana UI

Open a browser and navigate to:

```
http://<kibana-server-ip>:5601
```

You should see the Kibana home page.

---

### Step 2: Create an Index Pattern (Data View)

1. Go to **Management → Stack Management**
2. Select **Data Views**
3. Click **Create data view**
4. Enter index pattern (example):

   ```
   application-logs-*
   ```
5. Select the time field (e.g., `@timestamp`)
6. Save the data view

---

## 4. Creating Log Visualizations

### Example: Discover Logs

* Navigate to **Discover**
* Select the created data view
* Filter logs by time, log level, or message content

---

### Example: Create a Visualization

1. Go to **Visualize Library**
2. Click **Create visualization**
3. Choose visualization type (e.g., Bar chart, Pie chart)
4. Select the data view
5. Configure:

   * X-axis: Time (`@timestamp`)
   * Y-axis: Count of logs
6. Save the visualization

---

### Example: Create a Dashboard

1. Go to **Dashboard**
2. Click **Create dashboard**
3. Add saved visualizations
4. Save the dashboard for ongoing monitoring

---
