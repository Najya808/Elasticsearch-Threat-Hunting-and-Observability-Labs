# Lab 19: Intro to Elastic Security (SIEM) App

## Objectives
- Understand and navigate the Elastic Security (SIEM) app in Kibana.
- Analyze data through various views such as Hosts, Network, and Timelines.
- Learn how to utilize SIEM functionalities to improve security posture.

## Prerequisites
- Basic understanding of Security Information and Event Management (SIEM).
- Fundamental knowledge of the Elastic Stack (Elasticsearch and Kibana).
- Elastic Stack set up with version 7.x or later.
- Ingested data into Elasticsearch.

## Lab Tasks

### Task 1: Access the Security (SIEM) app in Kibana
**Open Kibana Dashboard**  
Launch your web browser and navigate to Kibana (http://localhost:5601).  
Log in using your credentials.

**Navigate to Security (SIEM) App**  
In the Kibana sidebar, click **Security** to access the SIEM application.

### Task 2: Explore the Hosts View
**Access Hosts Tab**  
Click on the **Hosts** tab. You should see a list of hosts with ingested data.

**Understanding Key Metrics**  
Observe metrics such as CPU usage, memory load, and disk I/O operations.  
Identify anomalies or spikes in resource usage.

**Example Analysis**  
Click on a host's name to view detailed activity and alerts related to that host.

### Task 3: Utilize the Network View
**Access Network Tab**  
Navigate to the **Network** tab to view network-related events.

**Interpret Network Data**  
Explore traffic metrics: inbound/outbound volume, IP connections, source/destination IP addresses.  
Identify potentially suspicious connections that might indicate threats.

**Case Study Example**  
A sudden increase in outbound traffic to an unfamiliar IP could indicate a data exfiltration attempt.

### Task 4: Create and Manage Timelines
**Access Timelines Tab**  
Click on the **Timelines** tab to create and review event timelines.

**Create a New Timeline**  
Use the **create timeline** feature to investigate a specific security incident.  
Add relevant data such as alerts, queries, and host activities.

**Example: Incident Investigation**  
Create a timeline for a login anomaly, including various events to trace activity flow.

### Task 5: Customizing and Saving Views
**Customizing Columns and Filters**  
Add or remove columns and apply filters to focus on specific data.

**Save Customized Views**  
Save these customizations for quick access in future sessions.

**Code Snippet for Query**  
Use Kibana Query Language (KQL) for advanced filtering:
```kql
host.name: "your-host-name" AND event.action: "login"
Conclusion

What I have learned: navigated the Elastic Security (SIEM) app in Kibana, explored Hosts, Network, and Timelines views, and used SIEM features to analyze security data effectively.
