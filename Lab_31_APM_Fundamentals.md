Lab 31 — APM Fundamentals
Objective

Understand the basics of Application Performance Monitoring (APM)

Install and configure an open-source APM agent in a sample application

Set up an APM server and visualize traces in a dashboard

Generate traffic to analyze transactions and performance metrics

Prerequisites

Working Node.js or Python development environment

Basic knowledge of terminal and CLI operations

Access to a server or local machine with administrative privileges

Basic understanding of application architecture

Task 1 — Install an APM Agent
Step 1.1 — Choose Application

Select either:

Node.js sample application

Python sample application

Ensure the application is running locally or on your server.

Step 1.2 — Install the APM Agent

Node.js

npm install elastic-apm-node --save

Python

pip install elastic-apm
Step 1.3 — Integrate the APM Agent

Node.js (app.js)

var apm = require('elastic-apm-node').start({
  serviceName: '<Your-Service-Name>',
  serverUrl: 'http://localhost:8200'
});

Python (app.py)

from elasticapm.contrib.flask import ElasticAPM
from flask import Flask

app = Flask(__name__)
apm = ElasticAPM(app, service_name='<Your-Service-Name>', server_url='http://localhost:8200')
Task 2 — Configure the APM Server in Kibana
Step 2.1 — Access Kibana

Log in to the Kibana web interface with administrative privileges.

Step 2.2 — Set Up APM Server

Navigate to: Stack Management → APM

Open APM Server Settings

Configure server URL and required parameters

Step 2.3 — Verify Configuration

Ensure application configuration matches Kibana APM settings

Restart the application to apply changes

Task 3 — Generate Traffic and Visualize Transactions
Step 3.1 — Simulate User Activity

Generate traffic using curl or Postman.

Example:

curl http://localhost:3000/
Step 3.2 — View Transactions in Kibana

Go to: Observability → APM

Analyze:

Response Time

Error Rate

Throughput

Transaction traces

Step 3.3 — Interpret Results

Identify performance bottlenecks

Detect slow transactions

Analyze error patterns

Determine optimization opportunities

What I Have Learned

Installed and configured an APM agent in a Node.js or Python application

Connected the application to an APM server

Generated traffic to collect performance data

Visualized and analyzed transaction traces in Kibana

Identified application performance bottlenecks
