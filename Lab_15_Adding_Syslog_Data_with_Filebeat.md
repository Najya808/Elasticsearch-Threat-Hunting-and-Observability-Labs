# Lab 15: Adding Syslog Data with Filebeat

## Objectives
- Understand how to configure Filebeat to collect syslog data.
- Learn to enable and configure the necessary modules within Filebeat.
- Ensure proper data ingestion into Elasticsearch.
- Utilize Kibana to search and analyze syslog events.

## Prerequisites
- Basic knowledge of ELK stack (Elasticsearch, Logstash, and Kibana).
- Familiarity with Linux command-line interface.
- A running ELK stack environment.
- Filebeat installed on the client machine.

## Materials Needed
- An ELK stack setup
- Filebeat installed on the system you’ll be collecting logs from
- A syslog service running on the system

## Lab Tasks

### Task 1: Enabling and Configuring Filebeat System Module
1. Navigate to the Filebeat modules directory:
   ```bash
   cd /etc/filebeat

Enable the system module to collect syslog and authorization logs:

sudo filebeat modules enable system

Edit the configuration file for the system module:

sudo nano modules.d/system.yml

Ensure the following configuration:

- module: system
  syslog:
    enabled: true
    var.paths: ["/var/log/syslog*"]
  auth:
    enabled: true
    var.paths: ["/var/log/auth.log*"]

Test the configuration for syntax errors:

sudo filebeat test config
Task 2: Start Filebeat and Confirm Data is Sent to Elasticsearch

Start the Filebeat service:

sudo service filebeat start

Verify Filebeat logs:

sudo tail -f /var/log/filebeat/filebeat

Ensure syslog data reaches Elasticsearch:

curl -X GET "localhost:9200/filebeat-*/_search?q=*&pretty"
Task 3: Visualizing Syslog in Kibana

Navigate to the Kibana web interface and go to Discover.

Filter or search syslog messages:

system.syslog.message: "*"

Create visualizations:

Go to Visualize in Kibana.

Use syslog data fields to create charts, graphs, and analyze patterns.

Conclusion

By completing this lab, you have successfully configured Filebeat to collect and forward syslog data to Elasticsearch. You verified data ingestion and explored syslog events in Kibana. These skills are fundamental for monitoring and analyzing log data in a production environment.

What I Learned

How to enable Filebeat system module for syslog collection.

How to configure module paths and test Filebeat configuration.

How to verify data ingestion in Elasticsearch.

How to search and visualize syslog events in Kibana.
