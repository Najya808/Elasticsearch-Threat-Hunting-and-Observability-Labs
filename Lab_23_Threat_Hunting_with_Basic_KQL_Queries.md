# Lab 23: Threat Hunting with Basic KQL Queries

## Objectives
- Understand the fundamentals of Kusto Query Language (KQL).
- Utilize KQL to perform basic threat hunting scenarios.
- Develop skills to analyze and filter logs for malicious activities.
- Familiarize with filtering techniques to identify outliers in data.
- Save, export, and share KQL queries for collaborative threat hunting.

## Prerequisites
- Basic knowledge of cybersecurity concepts.
- Familiarity with basic query languages is recommended.
- Access to an environment where KQL queries can be practiced (e.g., Azure Data Explorer or Log Analytics workspace).

---

## Task List
- Introduction to KQL and environment setup.
- Execute basic KQL queries to identify suspicious commands.
- Filter logs based on time parameters (outside business hours).
- Export and share KQL queries.

---

## Task 1: Introduction to KQL and Setting Up the Environment

### Overview
Kusto Query Language (KQL) is widely used in Microsoft Azure services for log analysis and monitoring. It is similar to SQL but optimized for querying structured and semi-structured log data.

### Step-by-Step

**Access your KQL environment:**
- Log in to the Microsoft Azure Portal.
- Navigate to Azure Data Explorer or a Log Analytics workspace.

**Review KQL basics:**
- Study KQL syntax and query structure.
- Explore official documentation for deeper understanding.

---

## Task 2: Execute Basic KQL Queries to Identify Suspicious Commands

### Objective
Detect potentially malicious command executions, such as PowerShell activity.

### Step-by-Step

**Open the logs section:**
- Navigate to Azure Monitor or your Log Analytics workspace.

**Execute a KQL query:**

```kql
SecurityEvent
| where process_command_line contains "powershell"

Interpret results:

Review key fields such as TimeGenerated, Account, and CommandLine.

Identify unusual or suspicious command patterns.

Refine the query:

Modify filters to search for additional suspicious keywords or behaviors.

Task 3: Filter Logs Based on Time Parameters (Outside Business Hours)
Objective

Identify suspicious events occurring outside normal business hours.

Step-by-Step

Apply a time-based filter:

SecurityEvent
| where process_command_line contains "powershell"
| where todatetime(TimeGenerated) between (datetime(2021-10-01T21:00:00Z) .. datetime(2021-10-02T06:00:00Z))

Analyze filtered logs:

Look for irregular login attempts or unusual command execution times.

Identify anomalies in user activity patterns.

Task 4: Export and Share KQL Queries
Objective

Export and share queries for reporting or team collaboration.

Step-by-Step

Export your query:

Use the Export option available in your Log Analytics workspace.

Save the query results or generate a shareable link.

Share findings:

Provide the exported file or link to team members for collaborative analysis.

Conclusion

What I have learned: used KQL to perform basic threat hunting, detected suspicious PowerShell executions, applied time-based filters to identify out-of-hours activity, and exported queries to support collaborative security investigations.
