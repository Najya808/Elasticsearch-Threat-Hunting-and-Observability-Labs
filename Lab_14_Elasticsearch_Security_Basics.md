Lab_14_Elasticsearch_Security_Basics.md
Objectives

Understand the fundamentals of securing Elasticsearch

Learn to create users with varying access privileges

Practice assigning roles and permissions in Elasticsearch

Implement secure access to indices in Elasticsearch

Prerequisites

Fundamental understanding of Elasticsearch and Kibana interfaces

Elasticsearch and Kibana installed and running

Access to the Elasticsearch and Kibana management console

Lab Tasks
Task 1: Creating Users with Limited Privileges
Step 1.1: Access Kibana Management Console

Open your web browser and navigate to your Kibana URL

Go to Stack Management in the left-hand menu

Step 1.2: Create a New User

Under Users/Roles, click Users

Click Create user

Fill out user details:

Username: limited_user
Password: (Ensure it meets your security policy)
Full Name: Limited User

Step 1.3: Assign Roles to the User

Scroll down to Roles

Click Add roles and select predefined roles such as viewer or a custom role granting limited read-only access

Step 1.4: Save the User Configuration

Click Create user to save the new user

Task 2: Verifying User Permissions
Step 2.1: Test User Access

Log out from the admin account in Kibana

Log in using limited_user credentials

Attempt to access an index via Kibana Discover

Step 2.2: Access Specific Indices

From the Kibana homepage, click Discover

Confirm that limited_user can only view documents in assigned indices

Restricted access messages indicate proper enforcement of permissions

Technical Highlight:
Users in Elasticsearch represent login entities. Each user must be assigned one or more Roles that define privileges for indices, clusters, or applications.

Case Study Example:
An e-commerce company creates multiple users: one with admin rights to manage Elasticsearch, and another with read-only access to daily order indices. This ensures the security and confidentiality of sensitive transaction data.

Example: Adding a Role via Elasticsearch API
PUT /_security/role/viewer_role
{
  "cluster": ["monitor"],
  "indices": [
    {
      "names": ["my_index"],
      "privileges": ["read"]
    }
  ]
}

Conclusion

By completing Lab 14, you have:

Learned to create users with restricted access

Assigned roles and privileges to users

Verified access restrictions in Kibana

Gained foundational skills to secure Elasticsearch data, maintaining integrity and confidentiality

What I Learned

Creating users in Elasticsearch

Assigning roles and privileges for security

Restricting index access to protect sensitive data

Testing and validating user permissions in Kibana

Using Elasticsearch API to manage roles programmatically
