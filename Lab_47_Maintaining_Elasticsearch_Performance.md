# Lab 47 — Maintaining Elasticsearch Performance

## Lab Objectives
- Understand how to monitor Elasticsearch cluster health.
- Learn to evaluate and optimize resource usage including disk, memory, and CPU.
- Explore strategies like Index Lifecycle Management (ILM) and index rollover to handle large datasets efficiently.

## Lab Prerequisites
- Basic understanding of Elasticsearch and its components.
- Access to an Elasticsearch cluster.
- Dev Tools enabled in Kibana.

---

## Lab Tasks

### Task 1: Monitor Cluster Health

#### 1.1 Check Cluster Health
**Objective:** Retrieve the cluster's health status to determine performance bottlenecks.

```http
GET /_cluster/health

Explanation:
The cluster health command checks overall status:

green: All primary and replica shards active.

yellow: Primary shards active, replicas unassigned.

red: Primary shards missing or unassigned.

Ensure the cluster is green for optimal performance.

1.2 Fetch Node Information

Objective: Gather details about each node to assess resource utilization.

GET /_cat/nodes?v

Explanation:
Lists nodes with:

Disk space

Memory usage

CPU load

This helps identify node-specific performance issues.

Task 2: Evaluate Resource Usage
2.1 Analyze Disk Usage

Monitor disk space percentage per node.

Identify indices consuming excessive storage.

Key Concept: Elasticsearch needs ≥15% free disk space to perform optimally.

2.2 Monitor Memory Usage

Command:

GET /_nodes/stats/jvm

Explanation:
Analyzes JVM heap memory:

used vs committed heap

Ensure heap <75% to avoid frequent Garbage Collection (GC).

2.3 Check CPU Load

Command:

GET /_nodes/stats/os

Explanation:
Monitors CPU load percentages.
High consistent CPU usage may indicate need for:

Additional shards

Adding new nodes

Task 3: Implement Data Management Strategies
3.1 Leverage Index Lifecycle Management (ILM)

Objective: Automate index management to optimize resources.

Example ILM Policy:

PUT _ilm/policy/logs_policy
{
  "policy": {
    "phases": {
      "hot": {
        "actions": {
          "rollover": {
            "max_size": "50gb",
            "max_age": "30d"
          }
        }
      },
      "delete": {
        "min_age": "90d",
        "actions": {
          "delete": {}
        }
      }
    }
  }
}

Explanation:

hot phase: Active indexing; rollover when size or age limit reached.

delete phase: Old data removed to free resources.

3.2 Use Index Rollover

Objective: Manage growing indices dynamically.

Command:

POST /<index-alias>/_rollover

Considerations:

Rollover based on document count or index size.

Integrates with ILM policies for automated index management.

Conclusion

In this lab, you learned to:

Monitor cluster health and node performance.

Evaluate disk, memory, and CPU usage for optimization.

Implement ILM policies and index rollover for efficient data management.
