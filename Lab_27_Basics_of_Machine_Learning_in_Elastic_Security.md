# Lab 27: Basics of Machine Learning in Elastic Security

## Objectives
- Understand the integration of Machine Learning (ML) within Elastic Security.
- Navigate and utilize ML features in Kibana.
- Enable and analyze prebuilt ML jobs to detect anomalies in security data.

## Prerequisites
- Basic understanding of Elastic Stack (Elasticsearch, Kibana).
- Elasticsearch and Kibana installed and running.
- Sample security data indexed into Elasticsearch.
- Access to the Kibana dashboard.

---

## Task List
- Navigate to the Machine Learning section in Kibana.
- Explore ML features such as Anomaly Detection.
- Enable a prebuilt ML job.
- Analyze detected anomalies.

---

## Task 1: Navigate to Machine Learning in Kibana

- Open Kibana in your browser (e.g., http://localhost:5601).
- From the left navigation panel, click on **Machine Learning**.
- Explore available options:
  - Anomaly Detection
  - Data Frame Analytics
  - Data Visualizer

---

## Task 2: Enable a Prebuilt ML Job – Anomalous Login Activity

### Navigate to Anomaly Detection
- Click on **Anomaly Detection** inside the Machine Learning section.
- Review available prebuilt ML jobs.

### Select and Enable Job
- Choose **Anomalous Login Activity**.
- Review job details.
- Click **Enable** to start processing data.

### Monitor Job Status
- Go to **Job Management**.
- Confirm status shows **Running**.
- Monitor processing progress.

---

## Task 3: Review and Analyze Detected Anomalies

### Access Anomaly Explorer
- Navigate to **Anomaly Explorer**.
- Review visual representations of detected anomalies.

### Analyze Results
- Identify unusual login patterns.
- Note severity scores and timestamps.
- Compare abnormal spikes against baseline behavior.
- Use visual graphs for deeper analysis.

---

## Conclusion

What I have learned: navigated Machine Learning features in Elastic Security, enabled a prebuilt anomaly detection job for login activity, monitored job execution, and analyzed detected anomalies to identify unusual security behavior.
