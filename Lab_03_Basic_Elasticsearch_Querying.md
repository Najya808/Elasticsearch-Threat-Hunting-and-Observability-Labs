Lab_Basic_Elasticsearch_Querying.md
Objectives

Understand the fundamentals of Elasticsearch querying

Learn how to list indices using Elasticsearch Cat APIs

Retrieve data using basic search queries

Use query parameters to refine search results

Prerequisites

Basic understanding of Elasticsearch architecture

Elasticsearch installed and running locally or access to a cloud instance

Familiarity with JSON structure

Access to terminal or Kibana Dev Tools

Lab Tasks
Task 1: List Indices Using Cat APIs
Objective

Learn how to list all indices in an Elasticsearch cluster.

Step 1.1: Perform GET Request

Open your terminal or Kibana Dev Tools and execute:

GET _cat/indices?v


If using terminal with curl:

curl -X GET "http://localhost:9200/_cat/indices?v"

Step 1.2: Analyze the Output

Observe the output table which contains:

health – Status of the index (green, yellow, red)

status – Whether index is open or closed

index – Name of the index

docs.count – Number of documents

store.size – Storage usage

Key Concepts

Green → All primary and replica shards are active

Yellow → Primary shards active, replica missing

Red → Some shards unavailable

Task 2: Retrieve Data Using a Simple Query
Objective

Use a basic search query to retrieve documents.

Step 2.1: Perform GET Request

Replace index_name with your index:

GET /index_name/_search


Using curl:

curl -X GET "http://localhost:9200/index_name/_search"


This retrieves all documents (default size: 10).

Step 2.2: Understand the Results

The response contains:

took → Time taken (ms)

hits.total → Total matching documents

hits.hits → Actual returned documents

_source → Original JSON document

Example:

GET /products/_search

Task 3: Experiment with Query Parameters
Objective

Refine search results using query parameters.

Subtask 3.1: Limit Results with size
GET /index_name/_search?size=5


This limits returned documents to 5.

Default value is 10.

Subtask 3.2: Use Simple Query with q Parameter

Search for keyword inside a specific field:

GET /index_name/_search?q=<field_name>:<keyword>


Example:

GET /products/_search?q=name:laptop


This searches documents where the name field contains "laptop".

Subtask 3.3: Analyze Query Effects

Change size value and observe differences

Modify field names and keywords

Notice how relevance score (_score) changes

Experimentation improves understanding of how Elasticsearch processes queries.

Conclusion

In this lab, we explored the fundamental concepts of querying in Elasticsearch. We learned how to list indices using Cat APIs, retrieve documents using simple search queries, and refine results using query parameters. These core querying skills are essential for effective log analysis, monitoring, and data exploration in cybersecurity and cloud environments.

What I Learned

How to use _cat/indices API

How to retrieve documents using _search

How query parameters like size and q refine results

Understanding of Elasticsearch response structure

Practical exposure to real-world data querying
