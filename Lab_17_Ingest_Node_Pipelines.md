# Lab 17: Ingest Node Pipelines

## Objectives
- Understand the functionality of Ingest Node Pipelines in Elasticsearch.
- Learn how to create and manage ingest pipelines using Kibana Dev Tools.
- Assign an ingest pipeline to an index using Filebeat or direct ingestion methods.
- Verify the effectiveness of your pipeline setup through Kibana Discover.

## Prerequisites
- Basic understanding of Elasticsearch and Kibana.
- Access to an Elasticsearch cluster.
- Kibana setup with necessary permissions.
- Filebeat installed and configured.

## Lab Tasks

### Task 1: Create an Ingest Pipeline
1. Open Kibana Dev Tools and click on **Dev Tools**.
2. Create a pipeline:
```json
PUT _ingest/pipeline/my_pipeline
{
  "description": "A pipeline to add a field and parse message",
  "processors": [
    {
      "set": {
        "field": "status",
        "value": "new"
      }
    },
    {
      "grok": {
        "field": "message",
        "patterns": ["%{COMMONAPACHELOG}"]
      }
    }
  ]
}

Processors: Units that perform transformations on incoming data.

Grok Processor: Parses unstructured log data into structured fields.

Execute the command (green Play button) to create the pipeline.

Task 2: Assign the Pipeline to an Index

Method 1: Using Filebeat

Edit filebeat.yml:

output.elasticsearch:
  hosts: ["localhost:9200"]
  pipeline: "my_pipeline"

Restart Filebeat:

sudo systemctl restart filebeat

Method 2: Direct Ingestion

Index a document through the pipeline:

POST my-index/_doc?pipeline=my_pipeline
{
  "message": "127.0.0.1 - - [14/Aug/2021:15:45:32 +0000] \"GET / HTTP/1.1\" 200 1234"
}
Task 3: Verify the Pipeline’s Effect

Open Kibana Discover.

Select your index (my-index) and verify:

The status field added by the pipeline.

Parsed message fields from the Grok processor.

Conclusion
What I have learned:

Created a simple ingest node pipeline using Kibana Dev Tools.
Assigned the pipeline to an index using Filebeat or through direct ingestion.
Verified the transformed data in Kibana Discover, ensuring my pipeline processes data as expected.
This lab demonstrated how ingest pipelines help in pre-processing data before indexing, an essential feature of Elasticsearch to optimize my data storage and search processes.

Verified the transformed data in Kibana Discover.

This lab demonstrates how ingest pipelines pre-process data before indexing, optimizing Elasticsearch storage and search efficiency.
