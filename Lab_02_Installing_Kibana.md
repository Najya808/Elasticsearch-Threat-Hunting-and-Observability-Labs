Lab_Installing_Kibana.md
Objectives

Understand the installation process of Kibana

Configure Kibana to connect with an Elasticsearch instance

Verify successful connectivity between Kibana and Elasticsearch

Prerequisites

Basic understanding of Elasticsearch and Kibana

Prior installation of an Elasticsearch instance

Terminal access (Linux, macOS, or Windows)

Administrative privileges

Lab Tasks
Task 1: Download and Install Kibana
Step 1: Verify Elasticsearch Installation

Ensure Elasticsearch is installed and running:

curl -X GET "http://localhost:9200/"


If Elasticsearch is running correctly, the output will display cluster information including version and cluster name.

Step 2: Download Kibana

Visit the official Kibana download page and download the appropriate version for your operating system:

👉 Kibana
👉 Elasticsearch

Step 3: Install Kibana
For Linux / macOS

Extract the downloaded file:

tar -xzf kibana-<version>-linux-x86_64.tar.gz


Navigate to the Kibana directory:

cd kibana-<version>-linux-x86_64

For Windows

Extract the downloaded .zip file

Navigate to the extracted Kibana folder

Task 2: Configure kibana.yml to Connect to Elasticsearch
Step 1: Open Configuration File

Navigate to the config directory inside the extracted Kibana folder.

Open:

config/kibana.yml

Step 2: Modify Elasticsearch Host

Edit the following setting:

# The URL of the Elasticsearch instance Kibana connects to
elasticsearch.hosts: ["http://localhost:9200"]


If authentication is enabled:

elasticsearch.username: "your_elasticsearch_username"
elasticsearch.password: "your_elasticsearch_password"


Save the file after making changes.

Task 3: Launch Kibana and Verify Connection
Step 1: Start Kibana
Linux / macOS
./bin/kibana

Windows
bin\kibana.bat

Step 2: Access Kibana in Browser

Open your browser and visit:

http://localhost:5601

Step 3: Verify Successful Connection

Kibana dashboard should load successfully

You should be able to access Elasticsearch data

Status page should show green "Connected"

Conclusion

In this lab, Kibana was successfully installed and configured to connect with an Elasticsearch instance. The connection was verified through the web interface, ensuring proper integration between both components. This setup forms the foundation for centralized log analysis, monitoring, and data visualization in cloud security environments.

What I Learned

How to install Kibana on different operating systems

How to configure kibana.yml to connect to Elasticsearch

How Kibana communicates with Elasticsearch

How to verify service connectivity and troubleshoot basic setup issues

The importance of centralized logging in cybersecurity environments
