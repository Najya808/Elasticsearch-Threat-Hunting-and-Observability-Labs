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

- [Lab 16 — Data Parsing with Logstash Grok](Lab_16_Data_Parsing_with_Logstash_Grok.md)
  Learned to configure Logstash with a Grok filter, parse unstructured logs, and forward structured data to Elasticsearch for visualization in Kibana.

- [Lab 17 — Ingest Node Pipelines](Lab_17_Ingest_Node_Pipelines.md)
  What I have learned: created ingest pipelines in Elasticsearch, assigned them to indices via Filebeat or direct ingestion, and verified transformed data in Kibana Discover.

- [Lab 18 — Data Retention with ILM (Index Lifecycle Management)](Lab_18_Data_Retention_with_ILM.md)  
  What I have learned: created and applied ILM policies in Elasticsearch, managed index lifecycle phases, and verified automatic index transitions in Kibana.

- [Lab 19 — Intro to Elastic Security (SIEM) App](Lab_19_Intro_to_Elastic_Security_SIEM_App.md)  
  What I have learned: navigated the Elastic Security (SIEM) app in Kibana, explored Hosts, Network, and Timelines views, and used SIEM features to analyze security data effectively.

- [Lab 20 — Host Overview in Elastic Security](Lab_20_Host_Overview_in_Elastic_Security.md)  
  What I have learned: navigated the Hosts section in Elastic Security, analyzed host activities, applied filters and queries to events, and saved queries for future use.

- [Lab 21 — Network Overview in Elastic Security](Lab_21_Network_Overview_in_Elastic_Security.md)  
  What I have learned: monitored inbound and outbound connections using Packetbeat, filtered network traffic by IPs and ports in Kibana, and documented suspicious or unexpected connections.

- [Lab 22 — Building Timelines for Investigations](Lab_22_Building_Timelines_for_Investigations.md)  
  What I have learned: created and managed investigation timelines using open-source tools, added and tagged events with notes, and visualized event sequences to support forensic analysis.

- [Lab 23 — Threat Hunting with Basic KQL Queries](Lab_23_Threat_Hunting_with_Basic_KQL_Queries.md)  
  What I have learned: used KQL to perform basic threat hunting, detected suspicious PowerShell activity, filtered logs based on time conditions, and exported queries for collaboration.

- [Lab 24 — Introduction to Detection Rules](Lab_24_Introduction_to_Detection_Rules.md)  
  What I have learned: explored and activated prebuilt detection rules in Elastic Security, simulated suspicious process execution, and verified alert generation within the SIEM.

- [Lab 25 — Custom Detection Rules](Lab_25_Custom_Detection_Rules.md)  
  What I have learned: created custom detection rules in Elastic, detected repeated failed login attempts using EQL, configured severity and risk scoring, set automated email alerts, and validated alerts through simulated authentication failures.

- [Lab 26 — Alerting & Actions in Kibana](Lab_26_Alerting_and_Actions_in_Kibana.md)  
  What I have learned: created alerts in Kibana, configured actions using an SMTP connector, defined trigger conditions for alerts, and verified email notifications for monitoring critical events.

- [Lab 27 — Basics of Machine Learning in Elastic Security](Lab_27_Basics_of_Machine_Learning_in_Elastic_Security.md)  
  What I have learned: navigated ML features in Elastic Security, enabled a prebuilt anomaly detection job for login activity, monitored job execution, and analyzed detected anomalies to identify abnormal security patterns.

- [Lab 28 — Observability Overview (Logs, Metrics, APM)](Lab_28_Observability_Overview_Logs_Metrics_APM.md)  
  What I have learned: explored observability concepts including logs, metrics, and APM; configured Prometheus, Elasticsearch, Kibana, and Jaeger; and monitored system performance using open-source tools.

- [Lab 29 — Centralized Logs View with Logs UI](Lab_29_Centralized_Logs_View_with_Logs_UI.md)  
  What I have learned: enabled and configured Filebeat on multiple Linux servers, shipped logs to Elasticsearch, accessed and navigated the Logs UI in Kibana under Observability, filtered logs in real-time using KQL by host and service, and analyzed centralized log data efficiently.

- [Lab 30 — Metrics UI for System Observability](Lab_30_Metrics_UI_for_System_Observability.md)  
  What I have learned: navigated the Metrics UI in an observability tool, monitored CPU, memory, and disk usage trends, interpreted performance spikes and anomalies, and analyzed detailed per-host metrics for system performance troubleshooting.

- [Lab 31 — APM Fundamentals](Lab_31_APM_Fundamentals.md)  
  What I have learned: installed and integrated Elastic APM agents in a Node.js or Python application, configured the APM server in Kibana, generated traffic to capture transactions, and analyzed response time, throughput, and error metrics through APM dashboards.

- [Lab 32 — Service Map Visualization in APM](Lab_32_Service_Map_Visualization_in_APM.md)  
  What I have learned: accessed and analyzed the Service Map in APM, identified service dependencies and call flows, examined response time and error metrics per service, and used distributed tracing to detect bottlenecks in a microservices environment.

- [Lab 33 — Synthetic Monitoring Basics](Lab_33_Synthetic_Monitoring_Basics.md)  
  What I have learned: configured browser-based synthetic monitoring using Heartbeat, simulated user journeys, analyzed monitor results in Kibana Uptime, identified failures and latency issues, and evaluated historical performance trends.

- [Lab 34 — Tracing with Distributed Traces](Lab_34_Tracing_with_Distributed_Traces.md)  
  What I have learned: implemented distributed tracing using OpenTelemetry, instrumented connected microservices, triggered end-to-end transactions, visualized traces in Jaeger, and analyzed latency and service dependencies to identify bottlenecks.

- [Lab 35 — Creating Custom Visualizations for Threat Hunting](Lab_35_Creating_Custom_Visualizations_for_Threat_Hunting.md)  
  What I have learned: created custom Kibana visualizations for threat hunting, filtered and analyzed security events by user or source IP, monitored high-count activities in short intervals, and organized visualizations into a dashboard for continuous monitoring.

- [Lab 36 — Field Mappings & ECS (Elastic Common Schema)](Lab_36_Field_Mappings_and_ECS.md)  
  What I have learned: mapped custom log fields to ECS equivalents, created an Ingest Node pipeline in Elasticsearch, and verified field mappings in Kibana Security and Observability apps to improve log management and analytics.

- [Lab 37 — Creating a Custom ECS Pipeline](Lab_37_Creating_Custom_ECS_Pipeline.md)  
  What I have learned: created a custom ECS ingest pipeline in Elasticsearch, applied it to Filebeat or Logstash, and verified ECS fields like client.ip and user.id in Kibana Discover and Security apps to standardize log data for observability and security.

- [Lab 38 — Kibana Canvas for Reporting](Lab_38_Kibana_Canvas_for_Reporting.md)  
  What I have learned: navigated Kibana Canvas, added and configured data sources from Elasticsearch indices, created interactive reports using text, shapes, and charts, and designed dynamic dashboards for security or observability monitoring.

- [Lab 39 — Historical Threat Analysis](Lab_39_Historical_Threat_Analysis.md)  
  What I have learned: analyzed historical event logs in Kibana, identified suspicious activities through process creation and network connection events, created a timeline of threats, and saved searches for ongoing monitoring and investigation.

- [Lab 40 — Exporting & Sharing Dashboards](Lab_40_Exporting_Sharing_Dashboards.md)  
  What I have learned: exported dashboards as PDF and CSV, generated shareable links, applied read-only permissions, and verified access to ensure secure distribution of dashboards.

- [Lab 41 — Trend Analysis Over Time](Lab_41_Trend_Analysis_Over_Time.md)  
  What I have learned: created time-series visualizations in Kibana, analyzed data trends over day/night periods, documented spikes and dips, and exported findings as reports to share with stakeholders.

- [Lab 42 — Using Watcher for Basic Alerting (OSS Basic)](Lab_Watcher_Basic_Alerting.md)  
  What I learned: configured a watch in Kibana Dev Tools to monitor critical errors, set up email/webhook actions, and tested alerts by injecting sample log data.

- [Lab 44 — Index Patterns & Field Customization in Kibana](Lab_44_Index_Patterns_Field_Customization.md)  
  What I learned: formatted numeric fields for readability, created a scripted field to combine `firstName` and `lastName`, and verified changes in Discover and Visualizations.

- [Lab 45 — Simple GeoIP Threat Hunting](Lab_45_Simple_GeoIP_Threat_Hunting.md)  
  What I learned: enriched IP logs with GeoIP data, visualized login attempts on a coordinate map, and detected unusual activity from unexpected regions using Kibana and Logstash.
