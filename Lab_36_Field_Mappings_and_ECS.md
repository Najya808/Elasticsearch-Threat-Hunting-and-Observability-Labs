# Lab 36 — Field Mappings & ECS (Elastic Common Schema)

## Objectives
- Understand the importance of Elastic Common Schema (ECS) in managing and interpreting log data.
- Learn how to map custom log fields to ECS equivalents.
- Verify the integration of ECS-mapped logs in Kibana's Security and Observability applications.

## Prerequisites
- Basic understanding of Kibana and Elasticsearch.
- Access to an Elasticsearch cluster with Kibana installed.
- Sample log data to work with.
- Basic knowledge of JSON and log formats.

---

## Task 1: Review ECS Field Definitions in Kibana

### Step 1: Accessing ECS Library
- Open Kibana and navigate to the Kibana Home dashboard.
- Go to Stack Management.
- Select Index Patterns and search for a pattern using ECS fields.

**Explanation:**  
The Index Patterns in Kibana represent data structures stored in Elasticsearch. Reviewing these patterns allows you to identify ECS field types and the corresponding data they store.

### Step 2: Explore ECS Field Documentation
- Visit the official [ECS documentation](https://www.elastic.co/guide/en/ecs/current/ecs-field-reference.html).

**Explanation:**  
Understanding ECS involves reviewing its field structures, such as `source.ip` and `process.name`, which standardize data representation across datasets.

---

## Task 2: Map Your Custom Log Fields to ECS Equivalents

### Step 1: Identify Custom Fields
- Review your custom log data and identify fields that can be mapped to ECS fields or require transformation.

**Example:**
```json
{
  "ip_address": "192.168.1.1",
  "user_process": "nginx"
}

Here, ip_address should map to source.ip and user_process to process.name.

Step 2: Create a Mapping Script

Use an Elasticsearch Ingest Node pipeline to transform logs:

PUT _ingest/pipeline/custom_log_pipeline
{
  "description": "Pipeline to map custom logs to ECS fields",
  "processors": [
    {
      "rename": {
        "field": "ip_address",
        "target_field": "source.ip"
      }
    },
    {
      "rename": {
        "field": "user_process",
        "target_field": "process.name"
      }
    }
  ]
}

Explanation:
Ingest Node pipelines preprocess documents before indexing. The rename processor remaps field names to ECS equivalents.

Task 3: Verify Your Logs in Security & Observability Apps
Step 1: Index Logs Using Pipeline
POST /your-index/_doc?pipeline=custom_log_pipeline
{
  "ip_address": "192.168.1.1",
  "user_process": "nginx"
}

Explanation:
Using the pipeline ensures your data is transformed and mapped to ECS upon indexing.

Step 2: Check Logs in Kibana Applications

Navigate to Kibana Security and Observability applications.

Verify if the logs appear with ECS fields recognized.

Case Study:
A company migrating legacy logs to ECS may see improved security alert efficiency due to normalized fields, allowing easier integration with visualization dashboards.

Conclusion

Successfully mapped custom log data to ECS equivalents.

Verified field mappings in Kibana's Security and Observability applications.

ECS standardization enhances log management, data correlation, and coherent analysis for reporting.
