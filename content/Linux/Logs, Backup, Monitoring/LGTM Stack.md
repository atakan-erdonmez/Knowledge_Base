---
tags:
  - monitoring
---
The LGTM stack is an open-source observability platform built by Grafana Labs. It's a comprehensive suite for monitoring applications and infrastructure, and the name is an acronym for the core components: Loki, Grafana, Tempo, and Mimir. 


You're already familiar with Grafana (G) as a visualization tool and Prometheus (a metric collector), so let's focus on the others and how they fit into the picture.  

## Loki (L) for Logs  

Loki is a log aggregation system that's designed to be highly scalable and cost-effective. Unlike traditional logging systems that index the full content of every log line, Loki only indexes metadata (labels), making it much more efficient for storage and faster for querying large volumes of logs. It's purpose-built to work with Grafana, allowing you to correlate logs with your metrics and traces in a single dashboard. This is a big step up from just having raw logs stored somewhere, as it helps you quickly pinpoint issues.  

## Tempo (T) for Traces  

Tempo is a distributed tracing backend that provides end-to-end visibility into the lifecycle of a request as it moves through a complex system. Think of it like a chain of breadcrumbs that follows a user's request from the moment it enters your application to the moment it leaves. Tempo helps you visualize this entire journey, so you can easily identify performance bottlenecks, latency issues, or failures across different services. It's especially useful for modern microservice architectures.  

## Mimir (M) for Metrics  

Mimir is a highly scalable, long-term storage solution for Prometheus metrics. While Prometheus is great at collecting and storing recent data, it's not designed for long-term storage or for a global view across multiple Prometheus instances. Mimir solves this by acting as a central hub where Prometheus servers can send their metrics. It offers massive scalability, high availability, and durable storage (usually on an object store like Amazon S3), allowing you to retain metrics for years and run queries on a global scale. In a way, Mimir is what "promotes" Prometheus from a short-term metrics collector to an enterprise-grade solution.  

## OpenTelemetry  

OpenTelemetry is a vendor-neutral set of APIs, SDKs, and tools for instrumenting your applications to generate and export telemetry data—metrics, logs, and traces. It's not part of the LGTM stack itself, but it's the glue that connects everything. Instead of using separate libraries for each tool, you can use OpenTelemetry to collect all three types of data in a standardized way and then send them to the appropriate components of your LGTM stack.  

These components work together to provide a complete view of your systems, known as observability. With the LGTM stack, you can use Grafana to visualize your Mimir metrics, view your Loki logs, and analyze your Tempo traces all from one central interface