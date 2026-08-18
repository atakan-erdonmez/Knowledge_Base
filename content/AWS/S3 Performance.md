---
link:
  - "[[S3]]"
---
S3 scales to high request rates with latency 100-200ms
- Applications can achieve at least 3,500 PUT/COPY/POST/DELETE or 5500 GET/HEAD requests per second per prefix in a bucket.
- There are no limits to the number of prefixes in a bucket.

### Prefix
- bucket/folder1/sub1/file => prefix is: /folder1/sub1
- bucket/folder2/sub2/file => /folder2/sub2
- bucket/1/file => /1/

> In order to increase performance, increase prefixes.


# Performance Optimization
## Multi-part Upload
It uses parallel upload to speed up transfers.
- Recommended for files > 100MB, necessary for files > 5GB

## S3 Transfer Acceleration
It uses edge locations to increase transfer speed. You upload the file to a close edge location, the it is transferred via AWS private line. 
- Compatible with multi-part upload
- Decrease the travel over Internet

It is great for **users that are far from bucket**. Improves both download and upload. Uses [[CloudFront]] network with edge locations. 
- If files up/downloaded are smaller than 1GB, it is better to use [[CloudFront]]'s PUT/POST commands for optimal performance.

## S3 Byte-Range Fetches
It works by parallelizing GETs by requesting specific byte ranges.
- Better resilience in case of failures
- Used for speed up downloads
- Can also be used to retrieve partial data (like only the head of the file)

> **It issues a Byte Range Fetch**, doesn't use SELECT statement