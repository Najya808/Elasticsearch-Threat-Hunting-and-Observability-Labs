Lab_Loading_Sample_Log_Data.md
Objectives

Understand how to prepare and structure a log file for analysis

Learn how to use Kibana’s file upload functionality or an Ingest Pipeline for data loading

Explore and verify the newly created index in Kibana Discover

Prerequisites

Basic knowledge of Elasticsearch and Kibana

Elasticsearch and Kibana installed and running

Access to Kibana web interface

Familiarity with JSON and text file formats

Lab Tasks
Task 1: Prepare Sample Log File
1.1 Create a Simple Log File

Using a text editor (VS Code, Notepad++, etc.), create a file named:

sample_logs.log


Add the following content:

[2023-10-05T13:45:30] [INFO] [APPLICATION] User login successful
[2023-10-05T13:46:12] [WARN] [DATABASE] Slow query detected
[2023-10-05T14:00:45] [ERROR] [APPLICATION] Exception thrown at module 3

Log Structure Explanation

Each log entry contains:

Timestamp

Log Level (INFO, WARN, ERROR)

Source (APPLICATION, DATABASE)

Message

Proper formatting ensures correct parsing during ingestion.

Task 2: Load Data into Kibana
2.1 Method 1 — Upload File via Kibana Interface

Using Kibana:

Step 1

Open Kibana in your browser:

http://localhost:5601

Step 2

Navigate to:

Machine Learning → Upload File

Step 3

Upload sample_logs.log using drag & drop or Browse.

Step 4

Follow ingestion wizard steps:

Review detected fields

Adjust field types if needed

Create index (e.g., sample_logs)

Complete import

2.2 Method 2 — Using an Ingest Pipeline (Advanced Method)

This method uses Elasticsearch API.

Step 1: Create an Ingest Pipeline

Open Kibana Dev Tools and run:

PUT _ingest/pipeline/log_pipeline
{
  "description": "Pipeline for ingesting log data",
  "processors": [
    {
      "grok": {
        "field": "message",
        "patterns": ["\\[%{TIMESTAMP_ISO8601:timestamp}\\] \\[%{LOGLEVEL:loglevel}\\] \\[%{WORD:source}\\] %{GREEDYDATA:message}"]
      }
    },
    {
      "date": {
        "field": "timestamp",
        "formats": ["yyyy-MM-dd'T'HH:mm:ss"]
      }
    }
  ]
}

Step 2: Index Log Data Using Pipeline
POST /logs/_doc?pipeline=log_pipeline
{
  "message": "[2023-10-05T14:00:45] [ERROR] [APPLICATION] Exception thrown at module 3"
}


This sends the log through the pipeline for parsing and indexing.

Task 3: Verify Data in Kibana
3.1 Check Newly Created Index

Navigate to Discover in Kibana

Create/select index pattern (e.g., logs* or sample_logs)

Verify:

Timestamp parsing

Log level field

Source field

Message field

Ensure logs appear correctly in the time range.

Conclusion

In this lab, we successfully created a structured log file and ingested it into Elasticsearch using two different methods: Kibana’s Upload File feature and a custom ingest pipeline. We verified proper parsing and indexing using Kibana Discover. This process forms the foundation of centralized logging and log analysis workflows in cloud security environments.

What I Learned

How to structure log files for ingestion

How Kibana’s upload feature works

How to build and use ingest pipelines

How Grok parsing extracts structured fields

How to verify indexed data in Discover

Importance of structured logging in SOC environments
