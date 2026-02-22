Lab_12_Introduction_to_Packetbeat.md
Objectives

Gain a basic understanding of Packetbeat and its functionalities

Learn how to install and configure Packetbeat

Enable DNS or HTTP modules and collect network flow data

Send and confirm data in Elasticsearch for visualization in Kibana

Prerequisites

Basic understanding of network protocols (DNS, HTTP)

Elasticsearch and Kibana installed and running

Root or sudo access on the system

Lab Tasks
Task 1: Install Packetbeat
Step 1.1: Ensure Elasticsearch and Kibana Are Running

Verify both services are active before proceeding.

Step 1.2: Download and Install Packetbeat

For Debian-based systems:

wget https://artifacts.elastic.co/downloads/beats/packetbeat/packetbeat-8.5.0-amd64.deb
sudo dpkg -i packetbeat-8.5.0-amd64.deb
packetbeat version


For RPM-based systems:

wget https://artifacts.elastic.co/downloads/beats/packetbeat/packetbeat-8.5.0-x86_64.rpm
sudo rpm -vi packetbeat-8.5.0-x86_64.rpm
packetbeat version

Task 2: Configure Packetbeat
Step 2.1: Locate Configuration File
sudo nano /etc/packetbeat/packetbeat.yml

Step 2.2: Set Elasticsearch Output
output.elasticsearch:
  hosts: ["http://localhost:9200"]


Add authentication if required.

Task 3: Enable DNS or HTTP Modules
Enable DNS Module
packetbeat.protocols.dns:
  ports: [53]

Enable HTTP Module
packetbeat.protocols.http:
  ports: [80, 8080, 8000, 5000, 8002]


Uncomment and adjust settings as needed for your environment.

Task 4: Start Packetbeat
Step 4.1: Start the Service
sudo systemctl start packetbeat

Step 4.2: Verify Service Status
sudo systemctl status packetbeat

Task 5: Verify Network Data in Elasticsearch
Step 5.1: Access Kibana

Open Kibana in your browser: http://localhost:5601

Step 5.2: Use Discover Feature

Navigate to Discover

Select the packetbeat-* index pattern to view incoming network logs

Step 5.3: Utilize Dashboards

Access pre-configured dashboards in the Dashboard section to visualize network traffic

Conclusion

By completing Lab 12, you have:

Learned the fundamentals of Packetbeat for network monitoring

Configured Packetbeat to capture DNS or HTTP traffic

Successfully forwarded network data to Elasticsearch

Visualized network metrics and flows in Kibana

This lab prepares you for advanced network analysis and troubleshooting using the Elastic Stack.

What I Learned

Installing Packetbeat on Linux systems

Configuring Elasticsearch output for log forwarding

Enabling DNS and HTTP modules to capture specific protocol traffic

Verifying Packetbeat service status and data ingestion

Visualizing network flow data using Kibana dashboards
