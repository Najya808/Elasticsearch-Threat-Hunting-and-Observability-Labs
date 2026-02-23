# Lab 16: Data Parsing with Logstash Grok

## Objectives
- Understand how to install and configure Logstash.
- Learn to create a Logstash pipeline using a Grok filter to parse log data.
- Output parsed data into Elasticsearch and verify data fields in Kibana.

## Prerequisites
- A machine with Linux or Windows OS.
- Java Development Kit (JDK) 8 or above installed.
- Basic understanding of Logstash, Elasticsearch, and Kibana.
- Elasticsearch and Kibana installed and running.

## Lab Tasks

### Task 1: Install Logstash
1. Download and install Logstash:

**Linux Users:**
```bash
wget https://artifacts.elastic.co/downloads/logstash/logstash-8.x.x-linux-x86_64.tar.gz
tar -xzf logstash-8.x.x-linux-x86_64.tar.gz

Windows Users:

Download the ZIP file from the official site.

Extract the contents using any archive manager.

Verify installation:

bin/logstash --version
Task 2: Create a Logstash Pipeline with a Grok Filter

Understand the Grok Filter:
Grok parses unstructured log data into structured fields.

Create configuration file logstash-grok.conf:

cd /path/to/logstash
nano logstash-grok.conf

Example basic configuration:

input {
  file {
    path => "/path/to/log/file.log"
    start_position => "beginning"
  }
}

filter {
  grok {
    match => { "message" => "%{COMBINEDAPACHELOG}" }
  }
}

output {
  elasticsearch {
    hosts => ["localhost:9200"]
    index => "logstash-%{+YYYY.MM.dd}"
  }
  stdout { codec => rubydebug }
}

Replace /path/to/log/file.log with your log file path.

Replace %{COMBINEDAPACHELOG} with a custom Grok pattern if needed.

Example for custom logs:

match => { "message" => "%{TIMESTAMP_ISO8601:timestamp} %{LOGLEVEL:loglevel} %{WORD:module} - %{GREEDYDATA:message}" }
Task 3: Output Data to Elasticsearch and Verify in Kibana

Start Elasticsearch and Kibana:

Linux:

sudo systemctl start elasticsearch
sudo systemctl start kibana

Windows:

Start both services via Services Manager.

Run the Logstash pipeline:

bin/logstash -f logstash-grok.conf

Verify in Kibana:

Open http://localhost:5601.

Navigate to Discover.

Ensure logstash-* index pattern is present.

Search logs and verify parsed fields.

Conclusion

By completing this lab, I have learned how to use Logstash’s Grok filter to parse and structure log data. I successfully output data to Elasticsearch and visualized structured logs in Kibana, enabling efficient log management and analysis in the ELK stack.
