---
link:
  - "[[AWS]]"
tag:
  - "[[00_KnowledgeBase/2- Tags/Databases|Databases]]"
---
Fully managed **graph** database

Amazon Neptune is a purpose-built, fully-managed graph database service optimized for storing billions of relationships and querying the graph with milliseconds latency. It supports highly connected data typical in social networking, recommendation engines, and fraud detection applications. Neptune provides a robust set of features, such as low-latency read replicas, high availability and durability with multi-AZ deployments, fault-tolerant and self-healing storage, continuous backups, encryption at rest, and it’s fully managed to ease setup and operation. It’s designed to offer fast reads across multiple regions and facilitates easy data recovery, making it suitable for applications requiring reliable, secure, and fast access to complex relational data (source from AWS features overview and detailed feature descriptions).


### What is Graph Database?
It is like a network of information:
- Like a social network, users have friends, posts have comments, comments have likes from users ...
- Everything is interconnected



- Highly available across 3 AZ, up to 15 read replicas
- Optimized for these complex and hard queries
- Can store up to billions of relations and query the graph with ms latency
- Gread for knowledge graphs (Wikipedia), fraud detection, recommendation engines, social networking...

## Neptune Streams
Real-time ordered sequence of every change
- Changes are available immediately after writing
- No duplicates, strict order
- Accessible with REST API

Use cases:
- Send notifications when changes made
- Make your graph sync to other data stores (S3, OpenSearch..)
- Replicate data across regions in Neptune

---
Neptune Streams is a feature within Amazon Neptune that allows for the capture of changes made to graph data in real-time. It reliably logs every change to the graph as it happens, in the order it is made, making these changes accessible via an HTTP REST API. This capability is crucial for applications that require real-time, consistent, and ordered change data capture, and it enables scenarios such as real-time recommendations, fraud detection, and social feeds.