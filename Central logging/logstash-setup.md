
---

## Installing and Configuring Logstash for Log Processing

### Prerequisites

* Elasticsearch installed and running
* Linux system (Ubuntu 20.04+ recommended)
* Open ports:

  * Logstash input ports (e.g., 5044 for Beats)
  * Elasticsearch port (9200)

---

## 1. Installation Instructions

### Option A: Install Logstash on Ubuntu (APT – Recommended)

1. **Add Elastic GPG key**

```bash
curl -fsSL https://artifacts.elastic.co/GPG-KEY-elasticsearch | sudo apt-key add -
```

2. **Add Elastic repository**

```bash
echo "deb https://artifacts.elastic.co/packages/8.x/apt stable main" | \
sudo tee /etc/apt/sources.list.d/elastic-8.x.list
```

3. **Update and install Logstash**

```bash
sudo apt update
sudo apt install logstash
```

---

### Option B: Install Using Docker (Optional)

```bash
docker run -d --name logstash \
-p 5044:5044 \
-v $(pwd)/logstash.conf:/usr/share/logstash/pipeline/logstash.conf \
docker.elastic.co/logstash/logstash:8.x
```

---

## 2. Example Logstash Configuration (`logstash.conf`)

The configuration file defines **inputs**, **filters**, and **outputs**.

### Sample Configuration

```conf
input {
  beats {
    port => 5044
  }
}

filter {
  grok {
    match => {
      "message" => "%{TIMESTAMP_ISO8601:timestamp} %{LOGLEVEL:level} %{GREEDYDATA:message}"
    }
  }
  date {
    match => ["timestamp", "ISO8601"]
  }
}

output {
  elasticsearch {
    hosts => ["http://localhost:9200"]
    index => "application-logs-%{+YYYY.MM.dd}"
  }
  stdout {
    codec => rubydebug
  }
}
```

### Configuration Explanation

* **Input**: Accepts logs from Beats on port 5044
* **Filter**: Parses timestamps and log levels
* **Output**: Sends logs to Elasticsearch and prints to console for debugging

---

## 3. Running Logstash and Sending Logs to Elasticsearch

### Step 1: Validate Configuration

```bash
sudo /usr/share/logstash/bin/logstash \
--path.settings /etc/logstash \
--config.test_and_exit \
-f /etc/logstash/conf.d/logstash.conf
```

Expected output:

```
Configuration OK
```

---

### Step 2: Start Logstash Service

```bash
sudo systemctl enable logstash
sudo systemctl start logstash
```

Check status:

```bash
sudo systemctl status logstash
```

---

### Step 3: Send Test Logs to Logstash

#### Using Filebeat (Example)

1. Install Filebeat:

```bash
sudo apt install filebeat
```

2. Configure Filebeat output:

```yaml
output.logstash:
  hosts: ["localhost:5044"]
```

3. Start Filebeat:

```bash
sudo systemctl start filebeat
```

---

### Step 4: Verify Logs in Elasticsearch

```bash
curl http://localhost:9200/application-logs-*/_search?pretty
```

Logs should appear in the search results.

---



