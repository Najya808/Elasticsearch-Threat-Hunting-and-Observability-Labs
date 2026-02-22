Lab_15_Adding_Syslog_Data_with_Filebeat.md
Objectives

Understand how to configure Filebeat to collect syslog data

Enable and configure required Filebeat modules

Ensure proper data ingestion into Elasticsearch

Utilize Kibana to search and analyze syslog events

Prerequisites

Basic knowledge of the ELK stack (Elasticsearch, Logstash, Kibana)

Familiarity with Linux command-line interface

A running ELK stack environment

Filebeat installed on the client machine

Lab Tasks
Task 1: Enabling and Configuring Filebeat System Module
Step 1.1: Navigate to Filebeat Directory
cd /etc/filebeat

Step 1.2: Enable the System Module
sudo filebeat modules enable system


This enables collection of syslog and authentication logs.

Step 1.3: Configure the System Module
sudo nano modules.d/system.yml


Ensure the following configuration is set:

- module: system
  syslog:
    enabled: true
    var.paths: ["/var/log/syslog*"]
  auth:
    enabled: true
    var.paths: ["/var/log/auth.log*"]

Step 1.4: Test Configuration
sudo filebeat test config


Confirms there are no syntax errors in the configuration.

Task 2: Start Filebeat and Confirm Data is Sent to Elasticsearch
Step 2.1: Start Filebeat
sudo service filebeat start

Step 2.2: Verify Filebeat Logs
sudo tail -f /var/log/filebeat/filebeat


Ensure there are no errors and logs are being shipped.

Step 2.3: Confirm Data in Elasticsearch
curl -X GET "localhost:9200/filebeat-*/_search?q=*&pretty"


Look for syslog entries in the output to verify successful ingestion.

Task 3: Visualizing Syslog in Kibana
Step 3.1: Access Discover

Open Kibana web interface

Navigate to Discover

Step 3.2: Filter Syslog Events

Use the search bar:

system.syslog.message: "*"


Adjust the time range and filters as needed.

Step 3.3: Create Visualizations

Go to Visualize in Kibana

Create charts or graphs using syslog fields

Analyze syslog patterns and trends

Conclusion

By completing Lab 15, you have:

Configured Filebeat to collect syslog and authentication logs

Verified successful ingestion into Elasticsearch

Explored and analyzed syslog data in Kibana

These skills are essential for monitoring, log analysis, and troubleshooting in production environments.

What I Learned

Enabling and configuring Filebeat system module

Collecting syslog and authentication logs

Validating Filebeat configuration

Confirming data ingestion in Elasticsearch

Searching and visualizing syslog data in Kibana
