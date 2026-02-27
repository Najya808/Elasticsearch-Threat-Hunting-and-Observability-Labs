# Lab 35 — Creating Custom Visualizations for Threat Hunting

## Objectives
- Understand the basics of threat hunting using data visualization.
- Learn to use Kibana to create custom visualizations for analyzing security events.
- Develop skills to filter data for anomalies or potential threats.
- Save and organize visualizations in a threat hunting dashboard for ongoing use.

## Prerequisites
- Basic understanding of cybersecurity principles and threat hunting.
- Familiarity with using Kibana.
- Access to a functioning ELK stack (Elasticsearch, Logstash, Kibana) with relevant security logs or demo data.

---

## Task 1: Setting Up Kibana
**Log into Kibana**
- Access your Kibana instance through your web browser.
- Ensure your Elasticsearch and Logstash are properly configured and running.

**Accessing Sample Data**
- If you don't have live data, load Kibana's sample data sets by navigating to "Sample Data" under the "Home" section.

---

## Task 2: Creating a Basic Visualization

### Subtask 2.1: Using Kibana Lens
- Navigate to "Analytics" > "Lens".  
- Select the relevant index containing security logs (e.g., firewall logs, network traffic).  
- Choose a visualization type: Bar chart, Line chart, or Pie chart.

### Subtask 2.2: Chart Events by Username or Source IP
- Drag the "Username" or "Source IP" field to the X-axis.  
- Drag a relevant metric (e.g., count of events) to the Y-axis.  
- Apply filters to focus on specific criteria, such as successful or failed logins.  

**Example Query Filter**
```json
{
  "query": {
    "bool": {
      "must": [
        { "match": { "log.type": "auth" } }
      ],
      "filter": [
        { "range": { "@timestamp": { "gte": "now-1d/d", "lt": "now/d" }}}
      ]
    }
  }
}
Task 3: Filtering for High Counts in Short Intervals

Use the time filter (top-right corner) to select a short interval (e.g., last 15 minutes).

Ensure Y-axis reflects count aggregation.

Add a filter to display high counts, indicating unusual activity.

Example Configuration

aggs:
  - terms:
      field: "user.keyword"
      size: 10
  - date_histogram:
      field: "@timestamp"
      fixed_interval: "15m"
  - top_hits:
      size: 10
      _source: ["host", "event"]
Task 4: Saving Custom Visualizations to a Dashboard

Click the “Save” button in the Lens editor.

Name your visualization (e.g., "High Login Attempts").

Navigate to "Dashboards" and create a new dashboard or edit an existing one.

Add your visualization using the "Add" button.

Arrange and resize panels for clarity.

Save the dashboard with an intuitive name (e.g., "Threat Hunting Dashboard").

Conclusion

By completing this lab, you can now:

Create custom visualizations in Kibana for threat hunting.

Identify unusual patterns in security logs.

Save and organize visualizations in a dedicated dashboard for ongoing monitoring.

Enhance your ability to investigate potential threats proactively.
