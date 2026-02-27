Lab 30 — Metrics UI for System Observability
Objective

Understand the importance of system observability through metrics

Navigate and interpret the Metrics UI

Gain insights into CPU, memory, and disk usage

Analyze detailed per-host metrics for deeper analysis

Prerequisites

Basic understanding of system metrics and monitoring

Access to an observability tool (e.g., Prometheus, Grafana, or similar)

Basic knowledge of command-line interface (CLI)

Introduction

System observability is critical in modern IT environments to ensure reliability, performance, and uptime.
This lab focuses on using the Metrics UI to monitor CPU, memory, and disk usage metrics, navigate the interface, and drill down into host-specific insights.

Task 1 — Open Metrics UI
Step 1.1 — Launch Browser

Open your preferred web browser and navigate to your observability tool URL. Example:

http://localhost:3000
Step 1.2 — Log In

Enter your credentials

If using default credentials (e.g., admin/admin), change the password immediately for security

Task 2 — Navigate to Metrics Section
Step 2.1 — Access Dashboard

Locate the sidebar menu

Navigate to:
Observability → Metrics

Step 2.2 — Explore Metrics UI

The dashboard should display panels such as:

CPU Usage

Memory Utilization

Disk Read/Write Rates

Familiarize yourself with graphs, charts, and tables showing usage over time.

Task 3 — Monitor CPU, Memory, and Disk Usage
Step 3.1 — Locate Usage Panels

Identify panels displaying:

CPU metrics

Memory metrics

Disk performance metrics

Step 3.2 — Interpret Metrics

CPU Usage

Identify spikes

Analyze processes contributing to high utilization

Memory Usage

Monitor for continuous growth

Detect potential memory leaks

Disk Usage

Observe read/write rates

Detect unusual activity or bottlenecks

Task 4 — Detailed Metrics by Host
Step 4.1 — Select a Host

Choose a specific host from the Metrics UI

Click the host name to open detailed metrics

Step 4.2 — Analyze Host Metrics

Review host-specific CPU, memory, and disk graphs

Identify abnormal trends or peak-hour resource spikes

Assess workload distribution and resource allocation

What I Have Learned

Navigated the Metrics UI within an observability tool

Monitored CPU, memory, and disk usage effectively

Identified performance spikes and potential resource issues

Analyzed detailed host-level metrics for troubleshooting
