Lab 29 — Centralized Logs View with Logs UI
Objective

Understand the implementation of a centralized logging system using the Logs UI in Kibana.

Enable and configure Filebeat to collect logs from multiple servers.

Filter and analyze logs based on host or service in real time using Kibana.

Prerequisites

Basic understanding of Linux command line

Familiarity with Elastic Stack (Elasticsearch, Kibana, Filebeat)

Linux environment with administrative access

Elasticsearch, Kibana, and Filebeat installed

Task 1 — Enable Filebeat on Multiple Servers
Step 1.1 — Install Filebeat
sudo apt-get update
sudo apt-get install filebeat -y
Step 1.2 — Configure Filebeat

Edit the configuration file:

sudo nano /etc/filebeat/filebeat.yml

Configure log input paths:

filebeat.inputs:
- type: log
  enabled: true
  paths:
    - /var/log/*.log

Configure Elasticsearch output:

output.elasticsearch:
  hosts: ["localhost:9200"]
Step 1.3 — Start and Enable Filebeat
sudo systemctl start filebeat
sudo systemctl enable filebeat
Task 2 — Access and Navigate Logs UI in Kibana
Step 2.1 — Access Kibana

Open:

http://localhost:5601
Step 2.2 — Navigate to Observability

Open Kibana dashboard

Go to Observability

Select Logs

This provides a centralized view of logs collected from multiple sources.

Task 3 — Filter Logs by Host or Service in Real Time
Step 3.1 — Filter by Host
host.name: "server1.example.com"
Step 3.2 — Filter by Service
service.name: "apache"
Step 3.3 — Advanced Filtering
host.name: "server1.example.com" AND service.name: "apache"
What I Have Learned

Configured Filebeat to collect logs from multiple Linux servers

Shipped logs to Elasticsearch

Accessed and navigated the Logs UI in Kibana

Used Kibana Query Language (KQL) to filter logs by host and service

Analyzed centralized logs in real time
