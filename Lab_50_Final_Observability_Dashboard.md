# Lab 50 — Final Observability & Threat Hunting Dashboard

## Lab Objectives
- Understand the basics of creating a comprehensive observability and threat-hunting dashboard.
- Learn to integrate various open-source tools to collect and visualize security alerts, CPU/memory usage, and network metrics.
- Develop the ability to present the final dashboard effectively for a Security Operations Center (SOC) as a single "pane of glass".

## Lab Prerequisites
- Basic knowledge of Linux command line and system administration.
- Understanding of networking fundamentals and security concepts.
- Familiarity with basic data visualization concepts.
- An environment set up with necessary open-source tools (e.g., ELK Stack, Grafana, etc.).

---

## Lab Tasks

### Task 1: Set Up Data Sources and Collectors

#### 1.1 Install and Configure Filebeat
**Purpose:** Ship log data to Elasticsearch.

```bash id="f1t2x0"
sudo apt-get update
sudo apt-get install filebeat

Configuration:
Edit filebeat.yml to specify log paths:

filebeat.inputs:
- type: log
  enabled: true
  paths:
    - /var/log/*.log
1.2 Configure Metricbeat for System Metrics

Purpose: Gather CPU and memory usage data.

sudo apt-get install metricbeat
sudo metricbeat modules enable system
sudo metricbeat setup
1.3 Setup Packetbeat for Network Metrics

Purpose: Collect and analyze network packet data.

packetbeat.protocols:
- type: flow
  enabled: true
  period: 10s
Task 2: Configure ELK Stack
2.1 Set Up Elasticsearch

Purpose: Store collected data.

sudo apt-get install elasticsearch
sudo systemctl start elasticsearch
sudo systemctl enable elasticsearch
2.2 Configure Logstash Pipelines

Purpose: Process incoming data and store in Elasticsearch.

Logstash Pipeline Config:

input {
  beats {
    port => 5044
  }
}

output {
  elasticsearch {
    hosts => ["localhost:9200"]
  }
}
sudo apt-get install logstash
sudo systemctl start logstash
sudo systemctl enable logstash
2.3 Install and Configure Kibana

Purpose: Visualize data collected in Elasticsearch.

sudo apt-get install kibana
sudo systemctl start kibana
sudo systemctl enable kibana

Access Kibana Dashboard:

Navigate to http://localhost:5601

Task 3: Create Dashboard
3.1 Create Dashboard Panels

Panels:

Security Alerts: Visualize alerts using Filebeat and Logstash data.

CPU/Memory Usage: Create time-series visualizations using Metricbeat system data.

Network Metrics: Display Packetbeat network flow data.

3.2 Add Event Timelines and Top Talkers

Event Timelines: Display logs chronologically for easy analysis.

Top Talkers: Identify the most active hosts in the network.

Task 4: Finalize and Present the Dashboard
4.1 Review for Consistency and Clarity

Ensure all data is visualized clearly and consistently.

Verify critical security events and system metrics are accessible.

4.2 Present as a Single Pane of Glass

Combine all visualizations into a cohesive dashboard view suitable for a SOC.

Conclusion

Successfully integrated and visualized security alerts, system performance metrics, and network data in a unified dashboard.

The dashboard serves as a holistic tool for observability and threat hunting in a Security Operations Center.

Continuous monitoring and updates enhance visibility into network and system activities.
