Lab 33 — Synthetic Monitoring Basics (Optional)
Objective

Understand the essentials of synthetic monitoring

Define a browser-based journey in Heartbeat configuration

Explore the Synthetic Monitoring UI in Kibana

Identify and analyze failures or high response times

Prerequisites

Basic knowledge of JSON and YAML

Familiarity with Kibana and Elastic Stack

Access to a system to install and run Heartbeat and Kibana

Installed Elasticsearch and Kibana

Task 1 — Define a Browser-Based Journey in Heartbeat
Step 1.1 — Install Heartbeat
sudo apt-get install heartbeat
Step 1.2 — Edit Heartbeat Configuration

Open the configuration file:

sudo nano /etc/heartbeat/heartbeat.yml
Step 1.3 — Define Browser Monitor Script

Add the following configuration:

heartbeat.monitors:
- type: browser
  name: "Sample E-Commerce Journey"
  id: synthetic-test-1
  schedule: '@every 1m'
  source:
    inline:
      script: |
        step('load homepage', async () => {
          await page.goto('https://example-ecommerce.com');
        });
        step('search product', async () => {
          await page.type('[data-test=search-box]', 'laptop');
          await page.click('[data-test=search-button]');
        });
        step('navigate to product', async () => {
          await page.click('[data-test=product-link]');
        });
Step 1.4 — Validate Configuration
heartbeat -e -c /etc/heartbeat/heartbeat.yml test config
Step 1.5 — Start Heartbeat
sudo service heartbeat start

Key Concept:
A browser monitor simulates a real user journey and records interactions with a web application.

Task 2 — Check Synthetic Monitoring UI in Kibana
Step 2.1 — Access Kibana

Open:

http://localhost:5601
Step 2.2 — Navigate to Uptime

Go to Observability → Uptime

View configured synthetic monitors

Step 2.3 — Verify Synthetic Tests

Confirm the synthetic journey appears in the monitor list

Check each step status

Ensure successful execution is reflected

Task 3 — Identify Failures or High Response Times
Step 3.1 — Analyze Monitor Results

Filter monitors with status down

Identify response times above thresholds

Step 3.2 — Debug Failures

Review detailed logs

Check captured screenshots

Identify failing steps

Example:
A missing UI element may indicate a website UI change.

Step 3.3 — Optimize High Response Times

Identify slow-loading actions

Review backend performance

Improve UI rendering efficiency

Step 3.4 — Historical Data Analysis

Use timeline/history view

Analyze performance trends over time

What I Have Learned

Configured a browser-based synthetic monitor using Heartbeat

Simulated user journeys for availability testing

Analyzed monitor results in Kibana Uptime

Identified failures and high response time issues

Used historical data to evaluate performance trends
