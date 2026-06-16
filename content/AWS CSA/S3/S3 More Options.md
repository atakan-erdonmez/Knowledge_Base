---
---
# Lifecycle Management
In S3, you can create lifecycle rules to move objects to different storage classes.
You can move current versions, non-current versions, delete non-current versions, expire current versions etc.

- It will work in background, and it will help decrease cost

# Requester Pays
Normally, bucket owner pays for storage and data transfer.
With requester pays, owner still pays for storage, but data transfer is paid by whomever did the download.
- The requester must be authenticated in AWS (cannot be anonymous)

# Event Notifications
Event examples: ObjectCreated, ObjectRemoved, Replication ...

It is used for automation. You can create workflows via sending data into SNS, SQS, or Lambda.

- You would need IAM permissions, like SNS Resources (Access) Policy

Additionally, you can set EventBridge. If you do, every event from S3 goes to Amazon EventBridge, which then can send it to over 18 AWS services. It has enhanced functionality. 


# Batch Operations
Perform bulk operations on existing S3 objects with a single request, like:
- Modify object metadata & properties
- Copy objects between S3 buckets
- Encrypt un-encrypted objects
- Modify ACLs, tags
- Restore objects from S3 Glacier
- Invoke Lambda function to perform custom action on each object



A job consists of a list of objects, the action to perform, and optional parameters

> S3 batch operations manages retries, tracks progress, sends completion notifications, generate reports etc

- You can use S3 Inventory to get object list and use Athena to query and filter your objects

# Route 53 Integration
When integration [[Route 53]] to S3 for static website hosting, the **S3 bucket name must match the domain name exactly**. 


> **Why?** When a user types your domain into a browser, Route 53 uses an **Alias record** to point to the S3 website endpoint. When S3 receives the HTTP request, it reads the Host header sent by the browser (e.g., `Host: www.example.com`) and looks for a bucket with that exact name to serve the content. If the names do not match, S3 will return a `404 Not Found` or `Access Denied` error.