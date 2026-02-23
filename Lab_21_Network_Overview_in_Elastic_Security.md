# Lab 21: Network Overview in Elastic Security

## Objectives
- Understand the basics of network monitoring with Elastic Security.
- Learn to use Packetbeat for capturing inbound and outbound connection data.
- Gain skills in filtering network traffic by IP addresses and ports.
- Identify and document any suspicious or unexpected connections in your network.

## Prerequisites
- Basic understanding of network concepts and security.
- An Elastic Stack environment (Elasticsearch, Kibana, and Packetbeat) up and running.
- Access to a terminal or command line interface.
- Basic knowledge of how to interact with the Kibana UI.

## Lab Tasks

### Task 1: Monitor Inbound/Outbound Connections using Packetbeat

**1.1 Install and Configure Packetbeat**  

**Step 1:** Ensure Packetbeat is installed on your system.  
```bash
sudo apt-get install packetbeat

Step 2: Configure Packetbeat to capture network traffic by editing packetbeat.yml:

packetbeat.interfaces.device: any
packetbeat.flows:
  timeout: 30s
  period: 10s

Step 3: Start the Packetbeat service and ensure it’s running:

sudo service packetbeat start

1.2 Visualize Network Traffic in Kibana

Step 1: Navigate to the Discover tab in Kibana.
Step 2: Filter the data source to show only Packetbeat data.
Step 3: Observe inbound and outbound connections and note key statistics such as IP addresses and protocols used.

Task 2: Filter Traffic by IP or Port

2.1 Use Kibana to Filter Data

Step 1: In Kibana, create a new filter in the Discover tab.

Step 2: To filter by IP address, use:

{
  "query": {
    "match": {
      "network.ip": "192.168.1.1"
    }
  }
}

Step 3: To filter by port, use:

{
  "query": {
    "match": {
      "network.port": 80
    }
  }
}

2.2 Customize and Save Filters

Step 1: Modify existing filters to capture specific events of interest.
Step 2: Save these filters for regular monitoring.

Task 3: Document Suspicious or Unexpected Connections

3.1 Identifying Anomalies in Network Traffic

Step 1: Use Kibana’s visualization tools to track uncommon destinations and sources.
Step 2: Employ time series analysis to detect traffic spikes or unusual patterns.

3.2 Document Findings

Step 1: Record any anomalous data points or patterns in a secure document.
Step 2: Include IP addresses, timestamps, and the nature of the activity.

Conclusion

What I have learned: monitored inbound and outbound connections using Packetbeat, filtered network traffic by IPs and ports in Kibana, and documented suspicious or unexpected connections.
