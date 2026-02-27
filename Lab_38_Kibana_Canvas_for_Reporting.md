# Lab 38 — Kibana Canvas for Reporting

## Objectives
- Learn how to navigate and use Kibana Canvas.
- Add and configure data sources in Kibana Canvas for security or observability indices.
- Design an interactive live report using shapes, text, and charts.

## Prerequisites
- Basic understanding of Elasticsearch and Kibana.
- Access to an Elasticsearch cluster and Kibana instance.
- Familiarity with creating and managing indices in Elasticsearch.

---

## Task 1: Open Canvas in Kibana

### Step 1.1: Navigate to Kibana Dashboard
- Open your web browser and go to your Kibana instance URL.
- Ensure you are logged in with credentials that have permissions to access Canvas.

### Step 1.2: Access Canvas
- In the Kibana main menu, click **Canvas**.
- If Canvas is not visible, verify your permissions or consult your administrator.

---

## Task 2: Add a Data Source for Your Security or Observability Index

### Step 2.1: Create a New Workpad
- Click **Create workpad** to start a new Canvas project.
- Provide a meaningful title for the workpad (e.g., "Security Observability Report").

### Step 2.2: Add a Data Source
- Click **Add element** in the workpad.
- Choose **Add Data** → **Index patterns**.
- Search for your index (e.g., `security-*`, `observability-*`) and select it.

### Step 2.3: Validate the Data Source
- Ensure the data from the index displays correctly (e.g., in a table or text element for verification).

---

## Task 3: Use Shapes, Text, and Charts to Create a Custom "Live Report"

### Step 3.1: Add Text Elements
- Click **Add element** → **Text**.
- Use Markdown to enhance text formatting:

```markdown
# Security Observability Live Report
**Date**: `{{date 'now'}}`
Step 3.2: Insert Shapes

Click Add element → Shapes.

Use rectangles, circles, or other shapes to highlight sections or separate areas.

Step 3.3: Create Charts for Data Visualization

Click Add element → choose a chart type (Bar, Line, Pie).

Configure each chart with the corresponding data series from your index.

Example code snippet to define a chart data query:

SELECT 
  DateHistogram(field='@timestamp', '1d') as HistoDate, 
  COUNT(*) as Events 
FROM "security-*"

Drag and drop the chart onto the Canvas and configure it using the panel on the right.

Step 3.4: Customize Report Layout

Adjust positioning and size of text, shapes, and charts.

Use drag-and-drop for precise placement and readability.

Conclusion

By completing this lab, you can:

Create a comprehensive, real-time report in Kibana Canvas.

Visualize key metrics and insights from security or observability indices.

Enhance reporting capabilities and provide stakeholders with a dynamic, data-driven dashboard.
