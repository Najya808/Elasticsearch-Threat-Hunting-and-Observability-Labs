# Lab 48 — Handling Large Log Volumes

## Lab Objectives
- Understand how to manage large volumes of log data effectively.
- Learn to utilize open-source tools for creating and managing data streams.
- Implement and verify data stream rollover conditions.

## Lab Prerequisites
- Basic understanding of log management concepts.
- Familiarity with Elasticsearch and Kibana.
- Access to an Elasticsearch instance (version 7.9+).

## Lab Setup
- Ensure Elasticsearch and Kibana are installed and running.
- Have access to a terminal or command-line interface.

---

## Lab Tasks

### Task 1: Create a Data Stream for a High-Volume Index Pattern

#### 1.1 Define an Index Template
Index templates define settings and mappings applied when a new index is created.

```http id="x1v9t0"
PUT _index_template/logs-template
{
  "index_patterns": ["logs-*"],
  "template": {
    "settings": {
      "number_of_shards": 1
    },
    "mappings": {
      "properties": {
        "@timestamp": {
          "type": "date"
        }
      }
    }
  },
  "data_stream": {}
}

Explanation:

index_patterns: Targets indices starting with logs-*.

@timestamp: Ensures the field is treated as a date for time-series data.

Task 2: Define Rollover Conditions
2.1 Create a Data Stream Rollover Policy
PUT _ilm/policy/logs-policy
{
  "policy": {
    "phases": {
      "hot": {
        "actions": {
          "rollover": {
            "max_size": "5GB",
            "max_age": "1d"
          }
        }
      }
    }
  }
}

Explanation:

rollover: Current write index transitions to a new index when:

Size > 5GB

Age > 1 day

2.2 Apply the Rollover Policy
PUT logs/_ilm/policy/logs-policy
Task 3: Confirm Data Stream Rollover
3.1 Insert Dummy Data
POST logs/_doc/
{
  "@timestamp": "2023-01-15T14:12:12",
  "message": "This is a log message",
  "level": "info"
}
3.2 Monitor Rollover
GET _cat/indices/logs-*?v

Explanation:

Ensures that a new index is created when rollover conditions are met.

Confirms the data stream is efficiently managing large log volumes.

Conclusion

By completing this lab, you have learned to:

Handle large volumes of log data using Elasticsearch data streams.

Define and apply rollover conditions to prevent resource overuse.

Monitor and verify that rollover occurs as intended.
