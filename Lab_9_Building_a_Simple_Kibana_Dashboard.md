Lab_9_Building_a_Simple_Kibana_Dashboard.md
Objectives

Understand the process of creating a new dashboard in Kibana

Incorporate existing visualizations into the dashboard

Enhance the dashboard with additional visualizations or saved searches

Prerequisites

Basic understanding of Kibana and its interface

Access to a running ELK (Elasticsearch, Logstash, Kibana) stack

Completion of Lab 8 – Creating Lens Visualizations

Lab Tasks
Task 1: Create a New Dashboard in Kibana
Step 1.1: Access Kibana

Open your web browser and navigate to your Kibana instance:

http://localhost:5601

Step 1.2: Open the Dashboard App

Click the Dashboard icon in the left-hand navigation pane.

Step 1.3: Create a New Dashboard

Click Create dashboard.

An empty canvas appears where you can add visualizations.

Step 1.4: Save Your Dashboard

Click the Save button (floppy disk icon) at the top-right corner.

Provide a name for your dashboard, e.g., Sample Dashboard.

Optional API Example:

POST /api/saved_objects/dashboard
{
  "attributes": {
    "title": "Sample Dashboard"
  }
}

Task 2: Add Existing Lens Visualization
Step 2.1: Search for Your Lens Visualization

On the dashboard canvas, click Add from library.

Use the search bar to locate the Lens visualization created in Lab 8.

Step 2.2: Add Visualization to the Dashboard

Select the desired visualization → click Add to dashboard.

Position it on the canvas using drag-and-drop.

Step 2.3: Adjust Visualization Settings

Click the visualization to modify its size and placement.

Rearrange using drag-and-drop for optimal layout.

Task 3: Add Additional Visualization or Saved Search
Step 3.1: Create Additional Visualization

Click Visualize Library → Create new visualization.

Select a chart type (Bar, Pie, Line, etc.) and configure with your dataset.

Step 3.2: Save the New Visualization

Click Save, provide a name, then return to your dashboard.

Step 3.3: Add New Element to Dashboard

Click Add from library → select your newly created visualization or a saved search.

Adjust layout, size, and placement to fit alongside existing content.

Conclusion

By completing Lab 9, you have:

Created a new Kibana dashboard

Added previously created Lens visualizations

Incorporated additional visualizations or saved searches

Designed a dashboard layout for multi-dimensional data analysis

This lab demonstrates the end-to-end process of building a functional Kibana dashboard, enabling effective monitoring and visualization of Elasticsearch data.

What I Learned

How to create and save dashboards in Kibana

Adding and positioning existing visualizations

Creating additional visualizations to enhance dashboards

Integrating saved searches into dashboards

Practical workflow for organizing and analyzing multiple data insights
