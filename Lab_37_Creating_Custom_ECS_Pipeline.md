# Lab 37 — Creating a Custom ECS Pipeline

## Objectives
- Understand the process of creating an ingest pipeline in Elasticsearch.
- Learn how to apply ECS (Elastic Common Schema) naming conventions using Kibana Dev Tools.
- Apply the pipeline to Filebeat or Logstash output.
- Verify the ECS fields in Kibana's Discover and Security apps.

## Prerequisites
- Basic knowledge of Elasticsearch, Kibana, and ECS.
- An operational Elasticsearch and Kibana instance.
- Installed Filebeat or Logstash.

---

## Introduction
This lab demonstrates how to create a custom Elasticsearch ingest pipeline to standardize log data according to the Elastic Common Schema (ECS). ECS ensures consistent field naming and structure across all Elastic products, making it easier to normalize and analyze data.

---

## Task 1: Define an Ingest Pipeline

### Step 1: Access Kibana Dev Tools
- Login to Kibana.
- Click on **Dev Tools** from the side navigation.

### Step 2: Create an Ingest Pipeline
```json id="ecs_pipeline_example"
PUT _ingest/pipeline/ecs_custom_pipeline
{
  "description" : "A pipeline for converting logs to ECS",
  "processors" : [
    {
      "rename": {
        "field": "client_ip",
        "target_field": "client.ip",
        "ignore_failure": true
      }
    },
    {
      "rename": {
        "field": "user_id",
        "target_field": "user.id",
        "ignore_failure": true
      }
    }
  ]
}

Explanation:

Ingest Pipeline: A series of processors executed on data as it is indexed.

Processors: Transform the data. Here, rename changes field names to follow ECS conventions.

Task 2: Apply the Pipeline to Filebeat or Logstash Output
Step 1: Configure Filebeat

Edit filebeat.yml to include the pipeline:

output.elasticsearch:
  hosts: ["http://localhost:9200"]
  pipeline: "ecs_custom_pipeline"
Or Step 1: Configure Logstash

In Logstash configuration:

output {
  elasticsearch {
    hosts => ["localhost:9200"]
    pipeline => "ecs_custom_pipeline"
  }
}

Explanation:
Specifying the pipeline ensures logs are processed through the ECS pipeline before indexing in Elasticsearch.

Task 3: Confirm ECS Fields in Kibana
Step 1: Verify in Discover

Go to Discover in Kibana.

Search for documents indexed by Filebeat or Logstash.

Verify that fields such as client.ip and user.id contain data.

Step 2: Verify in Security

Navigate to the Security app in Kibana.

Check that ECS fields client.ip and user.id are visualized correctly.

Conclusion

Created a custom ECS ingest pipeline in Elasticsearch.

Applied the pipeline to Filebeat or Logstash outputs for consistent log normalization.

Verified ECS fields in Kibana's Discover and Security apps.

Standardizing data with ECS improves search, correlation, and observability across multiple data sources in the Elastic Stack.
