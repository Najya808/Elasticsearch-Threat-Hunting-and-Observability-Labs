Lab 32 — Service Map Visualization in APM
Objective

Access and utilize the Service Map within Application Performance Monitoring (APM)

Identify and analyze service dependencies

Interpret key performance metrics for individual services

Prerequisites

Basic understanding of APM concepts

Access to an APM tool (e.g., Jaeger or Zipkin)

Running microservices sample application with tracing enabled

Task 1 — Open the Service Map in APM
Step 1.1 — Access APM Interface

Open your browser and navigate to your APM tool UI. Example for Jaeger:

http://<jaeger-host>:16686

Log in using your credentials.

Step 1.2 — Navigate to Service Map

Locate the Dashboard or Service Map section

Open the Service Map visualization

Task 2 — Identify Service Dependencies
Step 2.1 — Select the Test Service

Identify your target/test service node in the map

Service nodes represent individual services

Step 2.2 — Analyze Dependencies

Observe connecting lines between nodes

These represent service calls and dependencies

Understand request flow between services

Step 2.3 — Highlight Critical Paths

Use highlighting or filtering (if supported)

Focus on critical service-to-service interactions

Task 3 — View Service Performance Metrics
Step 3.1 — Click a Service Node

Select any service node to open detailed metrics.

Step 3.2 — Examine Metrics

Analyze metrics such as:

Response Time

Request Rate

Error Rate

Step 3.3 — Interpret Results

Identify latency spikes

Detect high error rates

Recognize bottlenecks

Determine areas needing optimization

Ingest Tracing Data (Example Setup)
Run Jaeger All-in-One with Docker
docker run -d --name jaeger \
    -e COLLECTOR_ZIPKIN_HTTP_PORT=9411 \
    -p 5775:5775/udp \
    -p 6831:6831/udp \
    -p 6832:6832/udp \
    -p 5778:5778 \
    -p 16686:16686 \
    -p 14268:14268 \
    -p 14250:14250 \
    -p 9411:9411 \
    jaegertracing/all-in-one:1.21
Enable Tracing in a Python Service (Jaeger Example)
from flask import Flask
from jaeger_client import Config

def initialize_tracer():
    config = Config(
        config={'sampler': {'type': 'const', 'param': 1}},
        service_name='your-test-service',
        validate=True,
    )
    return config.initialize_tracer()

app = Flask(__name__)
tracer = initialize_tracer()

@app.route('/')
def homepage():
    with tracer.start_span('homepage') as span:
        return "Welcome to the homepage!"
What I Have Learned

Accessed and navigated the Service Map in an APM tool

Identified service dependencies and request flows

Analyzed response time, request rate, and error rate metrics

Used tracing data to visualize service interactions

Recognized potential bottlenecks in microservices architecture
