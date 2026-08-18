---
link:
  - "[[00_KnowledgeBase/1- MOCs/AWS]]"
tag:
  - "[[CDN]]"
  - "[[Caching]]"
---
It is the CDN. Improves read performance by caching the content at the edge.

It has multiple origins (sources):
- [[S3]] bucket
	- Distributing files and caching
	- Uploading to S3
	- Secured using Origin Access Control (OAC, which basically controlls the permissions, turning a public access into a public -> OAC -> S3)
- [[VPC]] Origin
	- For applications hosted in VPC private subnets
	- ALB/NLB/EC2
- Custom Origin (HTTP)
	- S3 website (enable static S3 website)
	- Any public HTTP backend you want

## ALB or EC2 as an origin
The best way is to connect VPC private subnets to CloudFront. It will use VPC origin.
- This way, you don't have to expose anything on the Internet. CloudFront will use your VPC Origin to connect your Private Subnet

## Geo Restriction
You can restrict based on geolocation. You can use allowlist or blocklist. Country is determined using 3rd party Geo-IP database

## Price Classes
Prices differ between edge locations and total used data.
**Price Classes**:
1. All: all regions, best performance
2. 200: most regions, but excludes most expensive
3. 100: only least expensive regions

# Cache Invalidation
In order to change cached content, it should invalidate. You can wait for TTL or force an entire or partial cache refresh by *CloudFront Invalidation*.
- You can invalidate all files or special paths/prefixes


# Others
## Response Headers
CloudFront response headers policies simply tell which HTTP headers should be included or excluded in the responses sent by CloudFront.

### Origin Access Control (OAC)
**Origin Access Control (OAC)** is an AWS CloudFront security feature that locks down backend origins, most commonly S3 buckets or Lambda Function URLs, so they can only be accessed through your CDN, preventing users from bypassing CloudFront to reach your data directly. It secures this pipeline by automatically signing requests using AWS Signature Version 4 (SigV4), which allows the origin to verify CloudFront's identity via a bucket policy and reject all other traffic. As the modern successor to Origin Access Identity (OAI), OAC introduces critical enterprise upgrades, including full support for SSE-KMS encrypted buckets, newer AWS regions, and dynamic HTTP methods like `PUT` and `DELETE`.


--- 
# Index
```dataview
LIST
FROM ""
WHERE contains(link, [[CloudFront]])
```

