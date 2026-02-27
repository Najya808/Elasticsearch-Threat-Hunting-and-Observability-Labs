# Lab 46 — Basic EQL (Event Query Language) Usage

## Lab Objectives
- Understand the basic usage of Event Query Language (EQL).
- Learn to construct and execute simple EQL queries.
- Analyze and refine query results.

## Lab Prerequisites
- Basic knowledge of event logs and their importance.
- Access to a system with EQL-enabled tools (Elastic Stack or similar).
- Basic understanding of SQL-like query languages.

---

## Introduction
Event Query Language (EQL) is a powerful query language designed for searching event-driven data. It is often used in cybersecurity and system monitoring to detect sequences of events that might indicate malicious activity.

---

## Lab Tasks

### Task 1: Accessing EQL Tools
1. Open your Elastic Stack instance or a platform supporting EQL.
2. Navigate to **Dev Tools** or the **Security App** depending on your setup.
3. Ensure you have the necessary permissions to access event logs.

---

### Task 2: Writing an EQL Sequence Query

#### Step 1: Start a new EQL query
Example sequence query:

```eql
sequence
  [process where event.action == "start"]
  [network where event.action == "connection" and destination.port == 80]

Explanation:

sequence: Defines the order of events.

process: Specifies the type of event.

where: Filters events based on conditions.

Step 2: Analyze the query structure

Understand how events are linked sequentially.

Recognize the filter criteria for event selection.

Task 3: Running and Analyzing the Query

Execute the query using the "Run" button in your platform.

Review the returned results:

Check the timestamp of events.

Observe the source and context linking the process start to the network connection.

Task 4: Refining the Query
Step 1: Add conditions to make the query more precise

Example refined query:

sequence
  [process where event.action == "start" and process.name == "apache"]
  [network where event.action == "connection" and destination.port == 80]

Add filters like process.name or user for more targeted results.

Optionally, include time constraints to narrow down the analysis window.

Step 2: Re-run and analyze

Observe how additional conditions refine the output.

Understand how sequence queries can reveal patterns in system behavior.

Conclusion

This lab introduced the basics of using Event Query Language (EQL) for querying event logs. You learned to:

Construct simple EQL queries.

Interpret the results of sequences of events.

Refine queries for more precise threat detection.

EQL is a critical skill for cybersecurity professionals, enhancing the ability to detect and analyze system behaviors in event-driven environments.
