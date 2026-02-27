Lab 34 — Tracing with Distributed Traces
Objective

Implement Application Performance Monitoring (APM) using distributed tracing

Configure and install APM agents in connected microservices

Trigger and analyze an end-to-end transaction

Visualize trace data using open-source tools

Prerequisites

Basic understanding of microservices architecture

Familiarity with HTTP requests and web services

Development environment with Docker installed

Basic knowledge of Git

Task 1 — Setting Up Two Connected Services
Step 1.1 — Clone Repository
git clone https://github.com/example/distributed-tracing-lab
cd distributed-tracing-lab
Step 1.2 — Run the Services
docker-compose up --build

Ensure Docker and Docker Compose are installed and running.

Task 2 — Integrating APM Agents with OpenTelemetry
Step 2.1 — Modify Dockerfile for Service A
# Dockerfile inside Service A
FROM python:3.8-slim

RUN pip install opentelemetry-api opentelemetry-sdk opentelemetry-instrumentation

COPY . /app
WORKDIR /app

ENTRYPOINT ["opentelemetry-instrument", "python", "service_a.py"]
Step 2.2 — Modify Dockerfile for Service B
# Dockerfile inside Service B
FROM python:3.8-slim

RUN pip install opentelemetry-api opentelemetry-sdk opentelemetry-instrumentation

COPY . /app
WORKDIR /app

ENTRYPOINT ["opentelemetry-instrument", "python", "service_b.py"]
Step 2.3 — Rebuild and Restart Services
docker-compose down
docker-compose up --build
Task 3 — Trigger a Distributed Transaction
Step 3.1 — Initiate HTTP Request
curl http://localhost:<port_of_service_A>/api/trigger

Key Concept:
A distributed trace captures the complete execution path of a request as it travels across multiple services.

Task 4 — Visualize End-to-End Traces with Jaeger
Step 4.1 — Add Jaeger to docker-compose.yml
jaeger:
  image: jaegertracing/all-in-one:latest
  ports:
    - "6831:6831/udp"
    - "16686:16686"

Access Jaeger UI:

http://localhost:16686
Step 4.2 — Analyze Traces

Select your service from the dropdown

Click Find Traces

Examine spans representing Service A and Service B

Analyze latency and service hops

Observe:

Request duration

Span timings

Service dependencies

Bottlenecks

What I Have Learned

Configured distributed tracing using OpenTelemetry

Instrumented microservices with APM agents

Triggered and analyzed end-to-end transactions

Visualized traces using Jaeger

Identified latency issues and service bottlenecks
