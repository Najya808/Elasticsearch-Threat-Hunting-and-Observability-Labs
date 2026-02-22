Lab_6_Basic_Kibana_Discover_Usage.md
Objectives

Understand how to select an index in Kibana Discover

Adjust the time range for focused data analysis

Apply and manage filters to refine search results

Sort data effectively within Discover

Save a Discover view for future reference

Prerequisites

Basic knowledge of Elasticsearch and Kibana

Access to a Kibana instance connected to an Elasticsearch cluster

An existing index in Elasticsearch with data loaded

A web browser to access Kibana

Lab Tasks
Task 1: Select Your Index in Discover

Open Kibana in your web browser:

http://localhost:5601


Access the Discover tab from the left-hand sidebar.

Click the index dropdown at the top of the page.

Select the appropriate index to explore, e.g., logstash-*.

Key Concept: An index in Kibana represents a collection of related documents in Elasticsearch.

Task 2: Adjust the Time Range

Locate the Time Picker in the top-right corner.

Click to expand and select a predefined or custom range.

Example: Select Last 24 hours to focus on recent data.

Click Apply to filter the data accordingly.

Task 3: Add Filters

Locate the filter control panel just below the search bar.

Click Add a filter.

Select a field to filter by, e.g., status.

Define the condition, e.g., status is ERROR.

Click Save to apply the filter.

Key Concept: Filters narrow down search results to match specific criteria.

Task 4: Sort Results

Click the column header of the field to sort, e.g., timestamp.

Toggle ascending/descending order by clicking the header again.

Example Use Case: Sorting logs chronologically to visualize the most recent events first.

Task 5: Save a Discover View

Click the Save button at the top of the Discover page.

Enter a descriptive name for your saved search, e.g., Last 24 Hours Errors.

Click Save to store the configuration for future use.

Case Study: Saving frequently used views allows quick access to complex queries without recreating filters and settings.

Conclusion

By completing Lab 6, you have learned to:

Select indices in Kibana Discover

Adjust time ranges for focused analysis

Apply filters to refine results

Sort data efficiently

Save custom search views for repeated use

This foundational knowledge enhances your ability to interact with Elasticsearch data and prepares you for more advanced Kibana functionalities like dashboards and visualizations.

What I Learned

How to navigate Kibana Discover efficiently

Practical use of time filters for data analysis

Applying and managing filters for targeted searches

Sorting logs to prioritize recent events

Saving and reusing Discover views for workflow efficiency
