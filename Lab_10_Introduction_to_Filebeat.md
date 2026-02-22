Lab_10_Introduction_to_Filebeat.md
Objectives

Understand the basics of Filebeat and its role in the ELK stack

Learn how to install Filebeat on a machine

Configure Filebeat to monitor specific log files

Verify and ensure logs are successfully transferred to Elasticsearch

Prerequisites

Basic understanding of the ELK stack (Elasticsearch, Logstash, Kibana)

Admin access to a Linux-based machine (e.g., Ubuntu)

Elasticsearch installed and running

Basic command line knowledge

Introduction

Filebeat is a lightweight shipper for forwarding and centralizing log data. Installed as an agent on your servers, Filebeat monitors log files or locations that you specify, collects log events, and forwards them to Elasticsearch or Logstash. This lab guides you through setting up Filebeat to ship logs to Elasticsearch.

Lab Tasks
Task 1: Install Filebeat
Step 1.1: Add Filebeat Repository
curl -L -O https://artifacts.elastic.co/downloads/beats/filebeat/filebeat-oss-7.6.2-amd64.deb

Step 1.2: Install Filebeat
sudo dpkg -i filebeat-oss-7.6.2-amd64.deb

Task 2: Configure Filebeat
Step 2.1: Locate Configuration File
sudo nano /etc/filebeat/filebeat.yml

Step 2.2: Modify Log Path

Uncomment and specify the path to logs to monitor:

filebeat.inputs:
- type: log
  enabled: true
  paths:
    - /var/log/syslog

Step 2.3: Configure Elasticsearch Output

Ensure logs are sent to Elasticsearch:

output.elasticsearch:
  hosts: ["localhost:9200"]

Task 3: Start Filebeat Service
Step 3.1: Enable and Start Service
sudo systemctl enable filebeat
sudo systemctl start filebeat

Step 3.2: Verify Status
sudo systemctl status filebeat

Task 4: Verify Log Processing in Elasticsearch
Step 4.1: Check Filebeat Index
curl -X GET "localhost:9200/_cat/indices?v"


You should see an index like filebeat-*.

Step 4.2: Examine Logs via Kibana (Optional)

Navigate to Discover in Kibana.

Use the filebeat-* index to view ingested logs.

Conclusion

In this lab, you successfully installed and configured Filebeat to forward logs from a specified path to Elasticsearch. Running Filebeat as a service ensures continuous log collection for analysis and visualization, laying the foundation for a complete monitoring system with the ELK stack.

What I Learned

Installing and configuring Filebeat on a Linux system

Setting up log paths to monitor specific files

Configuring Filebeat to forward logs to Elasticsearch

Verifying log ingestion via Elasticsearch and Kibana

Running Filebeat as a persistent service for continuous logging
