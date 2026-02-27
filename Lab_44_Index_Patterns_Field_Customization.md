# Lab 44 — Index Patterns & Field Customization in Kibana

## Objectives
- Understand the basics of index patterns in Kibana.
- Learn to edit index patterns, focusing on field formatting.
- Create and utilize scripted fields to customize data presentation.
- Verify changes within Kibana's Discover or Visualize pages.

## Prerequisites
- Access to a working Kibana environment.
- Basic understanding of Elasticsearch and data indexing.
- Familiarity with JSON and scripting fundamentals.

---

## Lab Tasks

### Task 1: Editing an Index Pattern

#### Subtask 1.1: Access the Index Patterns
1. Open Kibana and navigate to **Stack Management**.
2. Under the **Kibana** section, click on **Index Patterns**.
3. Select the index pattern you want to edit.

#### Subtask 1.2: Format a Numeric Field
1. Locate the field you want to format (e.g., file size fields).
2. Click on the field to open editing options.
3. Find the **Format** dropdown and select **Bytes**.
   - Example: Format bytes to KB for storage size fields.
4. Save the changes.

---

### Task 2: Create a Scripted Field

#### Subtask 2.1: Define a Scripted Field
1. Within the same index pattern management page, click **Add scripted field**.
2. Enter a **Name** for the field, e.g., `FullName`.
3. Set **Language** to **Painless**.

#### Subtask 2.2: Write the Script
1. In the script editor, input:

```painless
return doc['firstName.keyword'].value + ' ' + doc['lastName.keyword'].value;

Click Save script to create the new field.

Task 3: Verify Changes in Discover or Visualizations
Subtask 3.1: Verify in Discover

Go to Discover in Kibana.

Choose your index pattern from the dropdown.

Check the Fields list to see your formatted and scripted changes.

View the data in a tabular form or add the fields to your query.

Subtask 3.2: Create a Simple Visualization

Navigate to Visualize.

Create a new visualization based on the modified index pattern.

Select a visualization type, e.g., Data Table.

Add your formatted or scripted fields.

Save the visualization and ensure fields display correctly.

Conclusion

You are now familiar with basic index pattern management in Kibana.

Learned to format fields for improved readability.

Successfully created a scripted field to combine or transform data.

Verified the changes in Discover and Visualize pages.

These skills optimize data exploration and presentation in Kibana.
