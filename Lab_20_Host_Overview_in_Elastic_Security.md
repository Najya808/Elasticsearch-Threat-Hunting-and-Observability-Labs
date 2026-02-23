# Lab 20: Host Overview in Elastic Security

## Objectives
- Understand the host overview feature in Elastic Security.
- Learn to navigate host-related events and activities.
- Gain skills in filtering and querying events.
- Save filters and queries for future reuse.

## Prerequisites
- Basic understanding of Elastic Stack.
- Access to an Elastic Security environment.
- Familiarity with Kibana's interface.

## Lab Tasks

### Task 1: Access the Hosts Section in Elastic Security
**Launch Kibana Dashboard**  
Open your web browser and navigate to the Kibana dashboard.

**Navigate to the Security App**  
Locate the sidebar on the left.  
Click **Security** to open the Elastic Security app.

**Access the Hosts Tab**  
Within Elastic Security, click on the **Hosts** tab.

### Task 2: Click on a Specific Host
**View the List of Hosts**  
In the Hosts tab, view all available hosts.

**Select a Host**  
Click on a host to get a detailed overview of its activities.

**Host Overview Analysis**  
Examine details such as active processes, user logins, and network activity associated with the selected host.

### Task 3: Filter Events by User or Process
**Locate the Events Section**  
While on a host’s detail page, navigate to the **Events** section.

**Apply Filters**  
Use the filter bar to specify parameters such as `user.name` or `process.name`.

**User Filter Example**
```json
{
  "query": {
    "match": {
      "user.name": "target_user"
    }
  }
}

Process Filter Example

{
  "query": {
    "match": {
      "process.name": "target_process"
    }
  }
}
Task 4: Save a Filter or Query for Reuse

Finalize the Filter or Query
Review the results to confirm the filter works as intended.

Save the Filter
Click the Save button in the filter bar.
Assign a name and description for easy identification later.

Reuse the Saved Filter
Navigate back to the filter bar, click Load Saved Filters, and select your previously saved filter.

Conclusion

What I have learned: navigated the Hosts section in Elastic Security, analyzed host activities, applied filters and queries to events, and saved queries for future use.
