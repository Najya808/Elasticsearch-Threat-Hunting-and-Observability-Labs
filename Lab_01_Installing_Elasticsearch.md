# Lab 01: Installing Elasticsearch

## Objectives
- Understand the requirements and setup necessary for Elasticsearch.
- Successfully install and configure Elasticsearch on your machine.
- Verify the installation and ensure Elasticsearch is running correctly.

## Prerequisites
- Basic understanding of Linux/Unix commands (for installation on Linux).
- Administrative rights to install software on your computer.
- Ensure Java Development Kit (JDK) 11 is installed on your system.
- Access to the command line interface (CLI).

## Lab Tasks

### Task 1: Download and Install Elasticsearch
**Subtask 1.1: Verify Java Installation**
```bash
java -version
Key Concept: Elasticsearch requires Java. Ensure you have JDK 11 installed.

Subtask 1.2: Download Elasticsearch

Navigate to the Elasticsearch Download Page.

Download the appropriate package for your operating system.

Subtask 1.3: Install Elasticsearch

Linux

wget https://artifacts.elastic.co/downloads/elasticsearch/elasticsearch-8.x.x-linux-x86_64.tar.gz
tar -xzf elasticsearch-8.x.x-linux-x86_64.tar.gz
cd elasticsearch-8.x.x
Windows

Extract the .zip file to the desired directory.

Key Concept: Ensure correct permissions are applied for the extracted directory on Linux.

Task 2: Configure elasticsearch.yml
Configurations are essential for customizing Elasticsearch behavior.

Subtask 2.1: Set Cluster Name

Open config/elasticsearch.yml and set:

cluster.name: my_cluster
Subtask 2.2: Configure Network Host

Set network host:

network.host: 0.0.0.0
Technical Term: network.host can be localhost for local access or 0.0.0.0 for remote access.

Task 3: Start the Elasticsearch Service
Subtask 3.1: Start Service

Linux

./bin/elasticsearch
Windows

Run elasticsearch.bat to start the service.

Subtask 3.2: Verify Elasticsearch is Running

curl -X GET "localhost:9200/"
Key Concept: This command retrieves cluster information and verifies Elasticsearch is responding.

Conclusion
You have successfully installed and configured Elasticsearch. You can now launch the service and verify its operation. This foundational setup is essential for subsequent tasks like data indexing and searching.

What I Learned
How to check and ensure Java JDK 11 is installed, which is required for Elasticsearch.

How to download and extract Elasticsearch on Linux and Windows.

Key configurations in elasticsearch.yml such as cluster name and network host.

How to start the Elasticsearch service and verify it using the CLI.

Understanding the basic structure of an Elasticsearch cluster and its accessibility settings.

