---
link:
  - "[[00_KnowledgeBase/1- MOCs/AWS]]"
---
It is the default bus, great for event-driven applications. You have resources that you get data from, and destinations to run actions. You can also use 3rd party partners' event bus

It is also a scheduling system. You can schedule events based on time, or an event pattern.

It can run a cron job every hour, or it can react to an event (IAM Root user sign in for example), and trigger a function, like Lambda or SQS message

- It is the only event-based service that can integrate with third-party SaaS partners


>**Amazon EventBridge (Amazon CloudWatch Events)** is a serverless event bus that makes it easy to connect applications together. It uses data from your own applications, integrated software as a service (SaaS) applications, and AWS services. This simplifies the process of building event-driven architectures by decoupling event producers from event consumers. This allows producers and consumers to be scaled, updated, and deployed independently. Loose coupling improves developer agility in addition to application resiliency.


- It can detect S3 events

## Schema Registry
EventBridge can analyze the events in the bus and infer the schema

Schema Registry allows you to generate code for your application, that will know in advance how data is structured in the event bus