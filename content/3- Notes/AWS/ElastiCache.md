---
link:
  - "[[AWS]]"
tag:
  - "[[Caching]]"
  - "[[00_KnowledgeBase/2- Tags/Databases|Databases]]"
---
It is a managed Redis or Memcached
- Reduces load off of a DB for read intensive workload
- AWS takes care of it, OS maintenance, patching, optimization etc
- **Using it required heavy application code changes**
- It is great for **read and compute intensive workloads**. It can also help with frequent short-live data interactions including writes.

- Applications queries ElastiCache, if not available, get from [[RDS]] and store in ElastiCache.
- Cache must have an invalidation strategy to make sure only the most current data is used in there, which makes it hard to set up

It can be used for session data, in user -> multiple sessions and apps


> Memcached supports Auto Discovery & multithreading
> Redis supports geospatial data
#### Use cases for high-frequency writes
**High-frequency, low-payload write workloads** are one of the absolute best use cases for Amazon ElastiCache (specifically using the **Redis/Valkey** engines).

Because your data payload is small but incoming at a massive rate, ElastiCache handles patterns like:

- **Real-Time Counters & Rate Limiters:** Tracking API request counts or page views (`INCRBY` / `HINCRBY`).
- **Gaming Leaderboards:** Constantly updating thousands of players' scores concurrently using Sorted Sets (`ZADD`).
- **IoT/Stream Data Ingestion:** Ingesting high-frequency, low-byte telemetry or activity tracking updates using Redis Streams (`XADD`).
- **Session & State Management:** Constantly updating shopping carts, user locations, or live status flags.

## Patterns
- **Lazy Loading**: all the read data is cached, data can become stale in cache
- **Write Through:** Adds or update data in the cache when written to a DB (no stale data)
- **Session Store:** store temporary session data in a cache (using TTL features)


Important ports
- PostgreSQL: 5432
- MySQL: 3306
- Oracle RDS: 1521
- MSSQL Server: 1433
- MariaDB: 3306 (same as MySQL)
- Aurora: 5432 (if PostgreSQL compatible) or 3306 (if MySQL compatible)

## Features
- Supports geospatial data types, making it perfect fit for storing and querying latitude and longitude data.