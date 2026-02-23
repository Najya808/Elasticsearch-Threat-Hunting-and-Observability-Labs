# Lab 18: Data Retention with ILM (Index Lifecycle Management)

## Objectives
- Understand the concept of Index Lifecycle Management (ILM) in Elasticsearch.
- Learn to create and apply an ILM policy effectively.
- Ensure smooth transition of indices through different lifecycle phases.

## Prerequisites
- Basic understanding of Elasticsearch and Kibana.
- Elasticsearch and Kibana installed and running.
- Access to Elasticsearch cluster with proper permissions.
- Relevant test indices exist or can be created.

## Lab Tasks

### Task 1: Create an ILM Policy in Kibana
**Step 1: Access Kibana Console**  
Open your web browser and navigate to the Kibana interface.  
Log in using your credentials.

**Step 2: Navigate to the Management Section**  
On the left pane, click **Management**.  
Under "Data", select **Index Lifecycle Policies**.

**Step 3: Create a New ILM Policy**  
Click **Create policy**.  
Enter a policy name, for example: `hot-warm-delete`.

**Step 4: Define Policy Phases**  
- **Hot Phase:**  
  Actions: no actions need to be specified unless required by your use case.  

- **Warm Phase:**  
  Toggle the Warm phase to include it.  
  Choose to migrate data to warm nodes if applicable.  

- **Delete Phase:**  
  Toggle the Delete phase to include it.  
  Set **Delete after** to 7 days.

**Step 5: Review and Save the Policy**  
Review the configured settings.  
Click **Save**.

### Task 2: Apply the ILM Policy to a Test Index
**Step 1: Access Index Management**  
Return to **Management** in Kibana.  
Select **Index Management** under "Data".

**Step 2: Choose a Test Index**  
Identify or create a test index (e.g., `test-index-001`).  
Click on the index to display its details.

**Step 3: Apply ILM Policy to the Index**  
Click **Manage ILM policy**.  
Select the created policy (`hot-warm-delete`) and confirm.

### Task 3: Confirm the Index Transitions in the ILM View
**Step 1: Monitor ILM Status**  
Return to **Index Lifecycle Policies**.  
View the applied policy details and monitor the index's current phase and history.

**Step 2: Validate Index Transition**  
Ensure the test index transitions through auto-managed phases according to the policy.  
*Note: Transitions might take time depending on the policy settings and index data.*

## Conclusion
What I have learned: created and applied ILM policies in Elasticsearch, managed index lifecycle phases, and verified automatic index transitions in Kibana.
