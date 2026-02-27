# Lab 28: Observability Overview (Logs, Metrics, APM)

## Objectives
- Understand key concepts of Observability in modern infrastructure.
- Explore interfaces for Logs, Metrics, and Application Performance Monitoring (APM).
- Gain hands-on experience with open-source observability tools.
- Learn how to monitor and troubleshoot applications using observability data.

## Prerequisites
- Basic understanding of software systems and cloud computing.
- Familiarity with command-line interface (CLI).
- Access to a Linux-based system with internet connectivity.

---

## Task List
- Install and explore observability tools.
- Configure log collection and visualization.
- Configure metrics monitoring.
- Explore Application Performance Monitoring (APM).

---

## Task 1: Introduction to Observability

### Overview
Observability refers to the ability to understand the internal state of a system by analyzing its outputs.

Core components:
- Logs
- Metrics
- Application Performance Monitoring (APM)

---

## Task 2: Explore Logs (Elasticsearch & Kibana)

### Install Elasticsearch

```bash
sudo apt-get update
sudo apt-get install elasticsearch
sudo systemctl start elasticsearch
sudo systemctl enable elasticsearch
Install Kibana
sudo apt-get install kibana
sudo systemctl start kibana
sudo systemctl enable kibana
Configure Filebeat to Send Logs
filebeat.inputs:
- type: log
  paths:
    - /var/log/*.log

output.elasticsearch:
  hosts: ["localhost:9200"]
Access Logs UI

Open Kibana at: http://localhost:5601

Create index patterns.

Explore logs dashboard.

Task 3: Explore Metrics (Prometheus & Grafana)
Install Prometheus
sudo apt-get update
sudo apt-get install prometheus
Configure Prometheus

Edit /etc/prometheus/prometheus.yml:

scrape_configs:
  - job_name: 'node'
    static_configs:
      - targets: ['localhost:9100']
Start Prometheus
sudo systemctl start prometheus

Access UI:
http://localhost:9090

Use the expression browser to query system metrics.

Optional Task: Application Performance Monitoring (APM)
Install Jaeger (Docker)
sudo docker run -d --name jaeger \
  -e COLLECTOR_ZIPKIN_HTTP_PORT=9411 \
  -p 5775:5775/udp \
  -p 6831:6831/udp \
  -p 6832:6832/udp \
  -p 5778:5778 \
  -p 16686:16686 \
  -p 14268:14268 \
  -p 14250:14250 \
  -p 9411:9411 \
  jaegertracing/all-in-one:1.30
Access Jaeger UI

http://localhost:16686

Analyze distributed traces to understand service interactions.

Conclusion

What I have learned: explored the core components of observability including logs, metrics, and APM; deployed and configured Prometheus, Elasticsearch, Kibana, and Jaeger; collected and visualized system data; and used observability tools to monitor and troubleshoot application performance.
