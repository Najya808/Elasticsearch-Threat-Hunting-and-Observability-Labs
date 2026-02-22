Lab_8_Using_Kibana_Lens_for_Basic_Visualization.md
Objectives

Understand how to navigate Kibana Lens for data visualization

Create a basic chart using Kibana Lens

Save and utilize visualizations for dashboard integration

Prerequisites

Basic knowledge of Elasticsearch and Kibana

A running Kibana instance (version 7.0 or later)

Access to a dataset indexed in Elasticsearch

Lab Tasks
Task 1: Open Kibana Lens

Log into your Kibana instance via web browser:

http://localhost:5601


Navigate to the Visualize Library from the side navigation panel.

Click Create visualization → select Lens as the visualization type.

Key Concept: Kibana Lens provides an intuitive drag-and-drop interface for creating visualizations quickly.

Task 2: Create a Basic Visualization
Step 2.1: Select a Dataset

Use the search bar to find your dataset (e.g., logs-*).

Choose the dataset for visualization.

Step 2.2: Drag a Field into the Editor

On the left panel, locate available fields from your dataset.

Drag a field (e.g., timestamp) onto the Drop a field here for your visualization area.

Lens will automatically suggest a chart type (e.g., Line Chart).

You can change the chart type to Line, Bar, Pie, etc.

Example: Dragging timestamp creates a Line Chart showing log counts over time.

Task 3: Customize Your Chart
Step 3.1: Use the Configuration Panel

Located on the right side of the Lens editor.

Modify aggregation type (Count, Average, Max, Median, etc.).

Step 3.2: Adjust the Time Range

Use the Time Filter in the top-right corner to specify a range (e.g., Last 7 days).

Task 4: Save and Export Your Visualization
Step 4.1: Save the Visualization

Click Save at the top of the Lens editor.

Enter a meaningful name, e.g., Log Count Over Time, and optionally a description.

Step 4.2: Add to Dashboard

After saving, choose to add to an existing dashboard or create a new dashboard.

This enables combining multiple visualizations for comprehensive data insights.

Conclusion

By completing Lab 8, you can now:

Access and navigate Kibana Lens

Create and customize basic visualizations

Save visualizations and integrate them into dashboards

These skills allow you to transform Elasticsearch data into actionable insights, preparing you for more advanced analytics and dashboard creation in Kibana.

What I Learned

Navigating Kibana Lens interface

Drag-and-drop creation of visualizations

Using configuration panel to modify chart type and aggregations

Applying time filters to control visualization scope

Saving visualizations and integrating them into dashboards

Translating raw log data into visual insights
