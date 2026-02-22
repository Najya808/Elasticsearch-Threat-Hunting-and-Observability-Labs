Lab_11_Introduction_to_Metricbeat.md
Objectives

Understand the role and functionality of Metricbeat in monitoring system and service metrics

Successfully install and configure Metricbeat

Collect and index CPU, memory, and other system metrics into Elasticsearch

Prerequisites

A Linux-based server with root or sudo access (Ubuntu 20.04 as reference)

Elasticsearch and Kibana set up and running

Basic command-line knowledge and familiarity with Elasticsearch concepts

Lab Tasks
Task 1: Install Metricbeat
Step 1.1: Import Elasticsearch GPG Key
wget -qO - https://artifacts.elastic.co/GPG-KEY-elasticsearch | sudo apt-key add -


Ensures that installed packages are legitimate and untampered.

Step 1.2: Add Metricbeat Repository
sudo sh -c 'echo "deb https://artifacts.elastic.co/packages/8.x/apt stable main" > /etc/apt/sources.list.d/elastic-8.x.list'


Replace 8.x with the appropriate release version if needed.

Step 1.3: Update Package List and Install Metricbeat
sudo apt update
sudo apt install metricbeat


Metricbeat is installed but not yet configured or running.

Task 2: Enable and Configure the System Module
Step 2.1: Enable the System Module
sudo metricbeat modules enable system


Collects system-level metrics: CPU, memory, disk IO, etc.

Step 2.2: Configure Metricbeat to Connect to Elasticsearch
sudo nano /etc/metricbeat/metricbeat.yml


Locate the output.elasticsearch section:

output.elasticsearch:
  hosts: ["http://localhost:9200"]


Include authentication if required in production environments.

Task 3: Start Metricbeat and Verify Metrics Collection
Step 3.1: Start and Enable Metricbeat Service
sudo systemctl start metricbeat
sudo systemctl enable metricbeat


Service starts Metricbeat immediately and ensures it runs on boot.

Step 3.2: Verify Metrics are Sent to Elasticsearch
sudo systemctl status metricbeat
curl -XGET 'http://localhost:9200/_cat/indices?v'


Look for indices prefixed with metricbeat-*.

Step 3.3: Visualize Data in Kibana

Open Kibana → Discover tab

Filter indices by metricbeat-*

Confirm that system CPU, memory, and other metrics are populated

Conclusion

By completing Lab 11, you have:

Installed and configured Metricbeat

Collected and sent system performance metrics to Elasticsearch

Verified data ingestion and visualized metrics in Kibana

Metricbeat’s modular design allows enabling additional modules for monitoring applications, services, and infrastructure, providing insights into system health and performance.

What I Learned

Installing Metricbeat on a Linux system

Enabling and configuring the system module

Connecting Metricbeat to Elasticsearch

Collecting CPU, memory, and disk metrics

Verifying Metricbeat data in Elasticsearch and Kibana

Using modular Metricbeat setup for monitoring multiple services
