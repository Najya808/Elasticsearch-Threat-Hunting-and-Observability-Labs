# Elasticsearch-Threat-Hunting-and-Observability-Labs
Hands-on lab exercises from the Alrazzaq internship focusing on Elasticsearch deployment, Elastic Security (SIEM), Kibana dashboards, log ingestion, threat detection, and observability using logs, metrics, and APM, aligned with CIS security best practices.

- [Lab 01 — Installing Elasticsearch](lab-01-installing-elasticsearch.md)
- Learn to download, install, and configure Elasticsearch, verify the service, and understand basic cluster and network settings. This foundational lab prepares you for all subsequent Elasticsearch exercises in threat hunting and observability.

- [Lab 02 — Installing Kibana](lab-02-installing-kibana.md)
- Installed and configured Kibana to connect with an Elasticsearch instance, verifying successful integration for centralized log visualization and analysis.

- [Lab 03 — Basic Elasticsearch Querying](lab-03-basic-elasticsearch-querying.md)
- Performed fundamental Elasticsearch queries including listing indices, retrieving documents, and refining results using query parameters for effective data exploration.

- [Lab 04 — Loading Sample Log Data](lab-04-loading-sample-log-data.md)
- Created structured sample logs and ingested them into Elasticsearch using Kibana upload and ingest pipelines, validating data parsing in Discover.

- [Lab 05 — Understanding Indices, Shards, and Replicas](lab-05-understanding-indices-shards-replicas.md)
- Created and explored custom indices in Elasticsearch with different shard and replica settings, analyzing their impact on performance and fault tolerance.

- [Lab 06 — Basic Kibana Discover Usage](lab-06-basic-kibana-discover-usage.md)
- Learned how to navigate Kibana Discover: selecting indices, applying filters, adjusting time ranges, sorting data, and saving custom search views for future use.

- [Lab 07 — Creating an Index Pattern](lab-07-creating-an-index-pattern.md)
- Created and validated an Elasticsearch index pattern in Kibana, enabling efficient data exploration and preparation for visualizations and dashboards.

- [Lab 08 — Using Kibana Lens for Basic Visualization](lab-08-using-kibana-lens-for-basic-visualization.md)
- Created basic visualizations in Kibana Lens, customized charts, applied time filters, and saved them for dashboard integration.

- [Lab 09 — Building a Simple Kibana Dashboard](lab-09-building-a-simple-kibana-dashboard.md)
- Built a simple Kibana dashboard, added existing Lens visualizations, and enhanced it with additional visualizations and saved searches for comprehensive data analysis.

- [Lab 10 — Introduction to Filebeat](lab-10-introduction-to-filebeat.md)
- Installed and configured Filebeat to monitor log files and forward them to Elasticsearch, ensuring logs are continuously collected for analysis and visualization.

- [Lab 11 — Introduction to Metricbeat](lab-11-introduction-to-metricbeat.md)
- Installed and configured Metricbeat to collect system metrics, including CPU and memory usage, and sent the data to Elasticsearch for monitoring and visualization in Kibana.

- [Lab 12 — Introduction to Packetbeat](lab-12-introduction-to-packetbeat.md)
- Installed and configured Packetbeat to capture network traffic, enabling DNS or HTTP module monitoring, and visualized the collected data in Elasticsearch and Kibana.

- [Lab 13 — Introduction to Heartbeat](lab-13-introduction-to-heartbeat.md)
- Installed and configured Heartbeat to monitor host uptime using ICMP pings and visualized monitoring data in Kibana.

- [Lab 14 — Elasticsearch Security Basics](lab-14-elasticsearch-security-basics.md)
- Learned to manage user roles and access privileges in Elasticsearch, ensuring secure and controlled access to indices through Kibana.

- [Lab 15 — Adding Syslog Data with Filebeat](Lab_15_Adding_Syslog_Data_with_Filebeat.md)
  Configured Filebeat to collect syslog data, ensured proper ingestion into Elasticsearch, and visualized syslog events in Kibana for effective monitoring and analysis.
