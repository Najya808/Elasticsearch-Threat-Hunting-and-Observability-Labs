Lab_13_Introduction_to_Heartbeat.md
Objectives

Understand the purpose and functionality of Heartbeat for system monitoring

Successfully install and configure Heartbeat on a Linux system

Set up and manage basic monitoring tasks, such as ICMP ping

Visualize monitoring results using Kibana

Prerequisites

Basic understanding of Linux command line

A running Elasticsearch and Kibana setup

Internet access for downloading Heartbeat

Introduction

Heartbeat is a lightweight shipper used for uptime monitoring. It can check the status of services using various protocols (e.g., HTTP, ICMP) and send that data to Elasticsearch for visualization in Kibana. This lab guides you through installation, configuration, and basic use of Heartbeat.

Lab Tasks
Task 1: Install Heartbeat
Step 1.1: Add Heartbeat Repository
wget -qO - https://artifacts.elastic.co/GPG-KEY-elasticsearch | sudo apt-key add -
sudo sh -c 'echo "deb https://artifacts.elastic.co/packages/7.x/apt stable main" > /etc/apt/sources.list.d/elastic-7.x.list'

Step 1.2: Install Heartbeat
sudo apt update
sudo apt install heartbeat-elastic

Task 2: Configure a Monitor
Step 2.1: Access Heartbeat Configuration File
sudo nano /etc/heartbeat/heartbeat.yml

Step 2.2: Setup ICMP Monitor
heartbeat.monitors:
- type: icmp
  schedule: '@every 10s'
  hosts: ["localhost"]  # Replace with target IP or hostname


This config checks the host every 10 seconds using ICMP ping.

Task 3: Validate Monitoring Results in Kibana
Step 3.1: Start Heartbeat
sudo service heartbeat-elastic start

Step 3.2: Enable Heartbeat on Boot
sudo systemctl enable heartbeat-elastic

Step 3.3: View Results in Kibana

Navigate to Kibana → Uptime app to view monitored hosts

Optionally, query the heartbeat-* index in Discover for raw monitoring data

Conclusion

By completing Lab 13, you have:

Installed and configured Heartbeat on a Linux system

Set up a simple ICMP monitor to track host availability

Verified and visualized monitoring data using Kibana

Heartbeat provides a foundation for monitoring uptime and service health, which can be extended to additional protocols and services.

What I Learned

Installing Heartbeat on Linux systems

Configuring ICMP monitors for uptime checking

Enabling Heartbeat to run as a persistent service

Using Kibana Uptime app for monitoring visualization

Querying raw heartbeat-* data in Kibana Discover
