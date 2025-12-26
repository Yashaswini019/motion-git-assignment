
---

## Installing and Configuring Elasticsearch for Log Storage

### Prerequisites

* Linux system (Ubuntu 20.04+ recommended)
* Java is bundled with Elasticsearch (no separate install required)
* At least **2 GB RAM** (4 GB recommended)
* Open ports: **9200** (HTTP), **9300** (transport)

---

## 1. Installation Instructions

### Option A: Install Elasticsearch on Ubuntu (APT – Recommended)

1. **Import the Elasticsearch GPG key**

```bash
curl -fsSL https://artifacts.elastic.co/GPG-KEY-elasticsearch | sudo apt-key add -
```

2. **Add the Elasticsearch repository**

```bash
echo "deb https://artifacts.elastic.co/packages/8.x/apt stable main" | \
sudo tee /etc/apt/sources.list.d/elastic-8.x.list
```

3. **Update package index and install Elasticsearch**

```bash
sudo apt update
sudo apt install elasticsearch
```

4. **Enable and start Elasticsearch**

```bash
sudo systemctl enable elasticsearch
sudo systemctl start elasticsearch
```

---

### Option B: Install Using Docker (Optional)

```bash
docker run -d --name elasticsearch \
-p 9200:9200 -p 9300:9300 \
-e "discovery.type=single-node" \
docker.elastic.co/elasticsearch/elasticsearch:8.x
```

---

## 2. Basic Configuration Settings (`elasticsearch.yml`)

The main configuration file is located at:

```bash
/etc/elasticsearch/elasticsearch.yml
```

### Minimal Configuration for Log Storage

```yaml
cluster.name: log-cluster
node.name: node-1

network.host: 0.0.0.0
http.port: 9200

discovery.type: single-node

path.data: /var/lib/elasticsearch
path.logs: /var/log/elasticsearch
```

### Important Configuration Notes

* `cluster.name`: Logical name for your Elasticsearch cluster
* `network.host`: Set to `0.0.0.0` to allow external access (secure in production)
* `discovery.type`: `single-node` is ideal for development or small setups
* `path.data` / `path.logs`: Define storage locations

After making changes, restart Elasticsearch:

```bash
sudo systemctl restart elasticsearch
```

---

## 3. Testing the Elasticsearch Installation

### Step 1: Check Service Status

```bash
sudo systemctl status elasticsearch
```

Expected result: **active (running)**

---

### Step 2: Test HTTP Connectivity

```bash
curl http://localhost:9200
```

Expected output (sample):

```json
{
  "name" : "node-1",
  "cluster_name" : "log-cluster",
  "cluster_uuid" : "xyz123",
  "version" : {
    "number" : "8.x.x"
  },
  "tagline" : "You Know, for Search"
}
```

---

### Step 3: Create a Test Index

```bash
curl -X PUT http://localhost:9200/test-logs
```

---

### Step 4: Insert a Sample Log Document

```bash
curl -X POST http://localhost:9200/test-logs/_doc \
-H "Content-Type: application/json" \
-d '{
  "timestamp": "2025-01-01T10:00:00",
  "level": "INFO",
  "message": "Elasticsearch log storage test successful"
}'
```

---

### Step 5: Search the Logs

```bash
curl http://localhost:9200/test-logs/_search?pretty
```

Expected result: The inserted log entry appears in the search results.


---

## 4. Next Steps

* Install **Logstash or Beats** to forward logs
* Secure Elasticsearch using authentication and TLS
* Connect **Kibana** for visualization
* Configure index lifecycle management (ILM)

---

