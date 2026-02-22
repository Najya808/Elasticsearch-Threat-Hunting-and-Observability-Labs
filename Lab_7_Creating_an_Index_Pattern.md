Lab_7_Creating_an_Index_Pattern.md
Objectives

Understand how to create and manage an index pattern in Elasticsearch

Configure an index pattern that matches your index name

Set a default time field and validate the pattern in Kibana Discover

Prerequisites

Basic understanding of Elasticsearch and Kibana

Running instances of Elasticsearch and Kibana

A dataset indexed in Elasticsearch (e.g., logs)

Access to the Kibana web interface

Lab Tasks
Task 1: Open Stack Management

Log into your Kibana interface:

http://localhost:5601


Navigate to the left sidebar → search for Stack Management → click to open.

Note: Stack Management centralizes control for managing Elasticsearch resources such as index patterns, saved objects, and Kibana settings.

Task 2: Create an Index Pattern
Step 2.1: Access Index Patterns

In Stack Management, under the Kibana section, select Index Patterns.

Explanation: Index patterns tell Kibana which indices to include when searching and visualizing data.

Step 2.2: Initiate Creation

Click Create index pattern.

Case Study: If your logs are stored in indices like logs-2023-01, logs-2023-02, etc., use the pattern:

logs-*

Step 2.3: Enter Index Pattern Name

Enter the index pattern name in the provided field.

Key Concept: The asterisk (*) acts as a wildcard to match multiple indices with similar naming patterns.

Task 3: Set a Default Time Field

Select a time field (usually @timestamp) from the dropdown.

This field will be used for time-based filtering and visualizations.

Click Create index pattern to finalize.

Explanation: The default time field enables chronological sorting and filtering in Discover and visualizations.

Task 4: Verify the Index Pattern in Discover

Navigate to Discover from the left sidebar.

Ensure your newly created index pattern appears in the index dropdown.

Select it and perform a basic search or apply a time filter to verify proper access and data mapping.

Explanation: Discover allows you to explore raw data, verify fields, and test queries using the new index pattern.

Conclusion

By completing Lab 7, you have:

Created an index pattern in Elasticsearch

Configured a default time field for chronological filtering

Verified data access and functionality in Kibana Discover

This foundational skill enables efficient data exploration, search, and visualization in the Elastic Stack, serving as a prerequisite for building dashboards and advanced analytics.

What I Learned

How index patterns work in Kibana

The role of wildcards (*) in matching multiple indices

Setting a default time field for time-based queries

Validating index patterns in Discover for effective data access

Preparing data for visualization and analysis
