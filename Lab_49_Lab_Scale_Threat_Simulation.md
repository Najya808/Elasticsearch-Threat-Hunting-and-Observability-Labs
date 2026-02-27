# Lab 49 — Setting Up a Lab-Scale Threat Simulation

## Lab Objectives
- Understand how to set up a lab-scale environment to simulate cybersecurity threats.
- Learn to use open-source tools for simulating threats.
- Analyze and interpret the data collected from these simulations.
- Investigate alerts in Kibana Security to understand potential threats.

## Lab Prerequisites
- Basic understanding of cybersecurity concepts and threat analysis.
- Familiarity with Linux command line.
- Access to a virtual or physical lab environment.
- Installed instances of Elasticsearch, Logstash, and Kibana (ELK Stack).

---

## Lab Tasks

### Task 1: Setup Lab Environment

#### 1.1 Launch Linux Virtual Machine
- Ensure you have a Linux VM up and running.
- Use platforms like VirtualBox or VMware Workstation.

#### 1.2 Install ELK Stack
- Follow the official ELK Stack installation guide for your Linux distribution.

---

### Task 2: Simulate Multiple Login Failures

#### 2.1 Create a Script for Simulating Login Failures

```bash id="x1v9t0"
#!/bin/bash

HOST="your.test.host"
USER="testuser"
PASSWORD="wrongpassword"

for i in {1..5}
do
  sshpass -p $PASSWORD ssh $USER@$HOST exit
done

Key Concept:

SSH Dictionary Attacks: This script simulates multiple failed SSH login attempts, commonly used in brute-force attacks.

Task 3: Confirm Log Ingestion and Trigger Alerts
3.1 Configure Logstash to Ingest Logs
input {
  file {
    path => "/var/log/auth.log"
    start_position => "beginning"
  }
}

filter {
  grok {
    match => { "message" => "%{SYSLOGTIMESTAMP:timestamp} %{SYSLOGHOST:host} %{DATA:process}: %{GREEDYDATA:message}" }
  }
}

output {
  elasticsearch {
    hosts => ["localhost:9200"]
    index => "ssh_access"
  }
  stdout { codec => rubydebug }
}
3.2 Setup Alerts in Kibana

Configure built-in detection rules for Failed Login Attempts in Kibana Security.

Task 4: Investigate Alerts in Kibana Security
4.1 Access Kibana Security Dashboard

Navigate to Kibana's Security section.

Review alerts triggered by the simulated login attempts.

4.2 Analyze Alert Data

Look for documents in the ssh_access index that match criteria set for triggering alerts.

Example Case Study:

Company XYZ noticed repeated login failures as a precursor to intrusion. By simulating threats, they adjusted alert severity, reducing incident response time.

Conclusion

This lab provides hands-on experience in setting up a lab-scale threat simulation.

You learned how simulated threat activities are monitored using ELK Stack.

Practicing these simulations helps improve incident response and tuning alert systems.
