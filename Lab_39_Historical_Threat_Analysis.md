# Lab 39 — Historical Threat Analysis

## Objectives
- Analyze historical data to identify potential threats.
- Utilize open-source tools for data investigation and threat identification.
- Develop skills to summarize suspicious activities effectively.

## Prerequisites
- Basic understanding of cybersecurity concepts.
- Familiarity with Kibana and Elastic Stack.
- Access to Kibana and associated data logs.
- Ability to execute basic command-line operations.

---

## Task 1: Setting Up the Environment

### Step 1.1: Install and Configure the Elastic Stack
- Ensure the Elastic Stack is installed. Follow the official Elastic installation guide if needed.
- Start the Elastic services:

```bash
# Start Elasticsearch
bin/elasticsearch

# Start Kibana
bin/kibana
Task 2: Selecting a Date Range in Kibana
Step 2.1: Access Kibana Dashboard

Open Kibana in a web browser (e.g., http://localhost:5601
).

Step 2.2: Define the Date Range

Navigate to the Discover tab.

In the date picker, select the desired range (e.g., "Last month").

Task 3: Investigating Event Logs
Step 3.1: Search for Process Creation Logs

Enter the following query in the search bar:

event.action:"process creation"

Key Concept: Process creation events indicate when new processes are spawned, which could signal malware or suspicious activity.

Step 3.2: Investigate Network Connections

Modify the search query:

event.category:"network" AND event.action:"connection"

Key Concept: Network connection logs help detect unauthorized access attempts or potential data exfiltration.

Task 4: Summarizing Suspicious Activities
Step 4.1: Create a Timeline

Navigate to the Timelines feature in Kibana.

Drag and drop relevant events to form a coherent timeline of suspicious activities.

Step 4.2: Save a Search

Perform a search for suspicious events.

Click Save and assign a meaningful name for future reference.

Key Concepts

Event Logs: Records documenting system activities, useful for audits and monitoring.

Kibana: Open-source data visualization tool for analyzing Elastic Stack data.

Threat Intelligence: Information on potential or ongoing threats for cybersecurity defense.

Conclusion

By completing this lab, you have:

Set up an environment to analyze historical data for threat detection.

Explored process creation and network connection logs to identify potential security breaches.

Created a timeline of suspicious activities in Kibana to summarize critical events.

Developed skills for effective historical threat analysis using open-source tools.
