# Lab 45 — Simple GeoIP Threat Hunting

## Lab Objectives
- Understand how to apply GeoIP enrichment on source IP addresses using open-source tools.
- Visualize geolocation data on a coordinate map.
- Identify unusual login attempts from unexpected regions.

## Lab Prerequisites
- Basic understanding of network security concepts.
- Familiarity with ELK stack (Elasticsearch, Logstash, and Kibana).
- Access to a running ELK stack setup.
- Basic knowledge of command-line interface (CLI) operations.
- Internet connection to download GeoIP databases.

---

## Lab Tasks

### Task 1: Prepare the Environment

#### 1.1 Install and Configure ELK Stack
- Ensure Elasticsearch, Logstash, and Kibana are running.
- Follow Elastic’s installation guide if not installed.

#### 1.2 Obtain GeoIP Database
- Download the free **GeoLite2** database from MaxMind.
- Extract the database to a directory accessible by ELK stack.

---

### Task 2: Setup Filebeat or Logstash for GeoIP Enrichment

#### 2.1 Configure Logstash
Create a `logstash.conf` in `/etc/logstash/conf.d/`:

```conf
input {
  file {
    path => "/path/to/your/log/file.log"
    start_position => "beginning"
  }
}

filter {
  geoip {
    source => "client_ip"
    target => "geoip"
    database => "/path/to/GeoLite2-City.mmdb"
  }
}

output {
  elasticsearch {
    hosts => ["localhost:9200"]
    index => "geoip-threat-hunting"
  }
  stdout { codec => rubydebug }
}

Key Concepts:

GeoIP: Maps IP addresses to geographical locations.

Filter Plugin: Used to enrich log data.

2.2 Start Logstash
sudo systemctl start logstash
2.3 Verify Data Ingress

Query Elasticsearch via Kibana.

Ensure logs contain geoip.location data.

Task 3: Visualize Data on a Coordinate Map
3.1 Access Kibana

Open: http://localhost:5601

3.2 Create a Coordinate Map

Navigate to Visualize Library > Create visualization > Maps.

Select the index pattern: geoip-threat-hunting.

Use geoip.location to plot IP addresses on the map.

Example Insight:

Visualize global login attempts.

Identify regions with high activity or anomalies.

Task 4: Identify Unusual Login Attempts
4.1 Anomaly Detection

Filter login attempts by region or number of attempts.

Highlight suspicious regions using Kibana queries.

4.2 Set Up Alerts

Use Elasticsearch Watches or Kibana Alerts.

Trigger notifications for high login attempts from unexpected locations.

Case Study:

A sudden spike from a high-risk country can indicate a threat.

Conclusion

Enhanced threat hunting using GeoIP enrichment of IP logs.

Visualized geolocation data on a coordinate map.

Identified anomalies and unusual login attempts.

Reinforces proactive threat detection.

Note: Regularly update the GeoIP database to maintain accuracy.
