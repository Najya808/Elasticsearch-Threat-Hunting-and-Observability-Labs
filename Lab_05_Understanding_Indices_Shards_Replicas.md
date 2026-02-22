Lab_Understanding_Indices_Shards_Replicas.md
Objectives

Understand the concepts of indices, shards, and replicas in Elasticsearch

Create and configure indices with custom shard and replica settings

Explore shard allocation and its impact on performance and fault tolerance

Prerequisites

Basic understanding of Elasticsearch architecture

Elasticsearch installed and running on local machine or server

Access to Kibana Dev Tools for executing queries

Lab Tasks
Task 1: Create a Custom Index with 1 Shard and 1 Replica
1.1 Access Kibana Dev Tools

Open Kibana in your web browser:

http://localhost:5601


Navigate to Dev Tools from the left-hand menu.

1.2 Create the Index

Execute the following command in Dev Tools:

PUT /my_custom_index
{
  "settings": {
    "index": {
      "number_of_shards": 1,
      "number_of_replicas": 1
    }
  }
}

Explanation

Index → Collection of related documents

Shard → Horizontal partition of index data, distributed across nodes

Replica → Copy of a shard used for fault tolerance

Task 2: View Shard Allocation
2.1 Shard Allocation

In Dev Tools, run:

GET _cat/shards/my_custom_index?v


Explanation:
This returns:

Shard ID

Index name

Node allocation

State (STARTED, UNASSIGNED)

Primary/Replica indicator

This helps understand where data is physically stored and its redundancy.

Task 3: Discuss Shard and Replica Settings Impact
3.1 Performance Impact

Shards: More shards allow queries to be distributed across nodes, improving search performance. Excessive shards can lead to overhead.

Replicas: Increase fault tolerance; writes take longer as replicas must be updated.

3.2 Fault Tolerance

Case Study:

A system storing daily user logs in one index

Multiple replicas ensure logs are accessible even if a server fails

Ensures application stability without downtime

Conclusion

By completing this lab, you have learned:

How to create indices with custom shard and replica settings

How shard allocation affects performance and fault tolerance

How to balance shards and replicas for efficient Elasticsearch deployments

What I Learned

Importance of shards for distributing data and improving search performance

Role of replicas in ensuring high availability

How to inspect shard allocation using _cat/shards

Impact of index configuration on real-world Elasticsearch deployments
