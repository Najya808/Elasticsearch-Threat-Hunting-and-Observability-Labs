# Lab 25: Custom Detection Rules

## Objectives
- Understand how to create and configure custom detection rules.
- Alert on repeated failed login attempts within a short timeframe.
- Configure rule severity, risk score, and actions.
- Test detection rules by simulating failed login attempts.

## Prerequisites
- Basic understanding of networking and security concepts.
- Access to Elastic Stack (ELK).
- Basic knowledge of YAML and JSON formats.
- A test environment to simulate login attempts.

---

## Task List
- Set up Elastic Stack environment.
- Create a custom detection rule.
- Configure severity, risk score, and alert actions.
- Simulate failed login attempts.
- Verify alert generation.

---

## Task 1: Setting Up the Environment

### Install Elastic Stack (ELK)

Ensure Elasticsearch, Logstash, and Kibana are installed and configured.

**Elasticsearch Configuration Example:**


network.host: 0.0.0.0


**Kibana Configuration Example:**


server.host: "0.0.0.0"
elasticsearch.hosts: ["http://localhost:9200"]


Create a test SSH environment with logging enabled to simulate failed login attempts.

---

## Task 2: Create Custom Detection Rule

### Objective
Detect repeated failed login attempts within a 5-minute timeframe.

### Step-by-Step

Navigate to:
Security → Detections → Create New Rule

Use Event Query Language (EQL):

```eql
event.category: authentication and event.type: failure
  | sequence by host.id, user.id
    [ authentication where event.outcome == "failure" ]
    [ authentication where event.outcome == "failure" ]
Task 3: Configure Rule Settings
Set Severity and Risk Score

Severity:

medium

Risk Score:

50
Configure Alert Action (Email)
actions:
  - action_type_id: .email
    config:
      from: "alerts@example.com"
      to: ["admin@example.com"]
      subject: "Repeated Login Failure Alert"
      message: "Multiple login failures detected."
Task 4: Test the Detection Rule
Simulate Failed Logins
#!/bin/bash
for i in {1..5}; do
  ssh invalid_user@localhost
done
Verify Alert

Navigate to:
Security → Detections → Alerts

Confirm that the custom detection rule triggered successfully.

Conclusion

What I have learned: created a custom detection rule in Elastic, used EQL to detect repeated authentication failures, configured severity and risk scoring, set up automated email alerts, and validated rule functionality through simulated failed login attempts.
