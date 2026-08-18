---
link:
  - "[[S3]]"
  - "[[KMS (Key Management Service)]]"
tag:
  - "[[00_KnowledgeBase/2- Tags/Security]]"
---
4 methods to encrypt objects

# Server-Side Encryption (SSE)
#### SSE with Amazon S3-Managed Keys (SSE-S3)
- Enabled by default, encrypt with keys handled, managed and owned by AWS
- Keys are managed by AWS. Encryption type is AES-256. 
- Header: "x-amz-server-side-encryption":"AES256"
- Enabled by default for new buckets & objects
- Rotation are invisible to the user, and you cannot modify

#### SSE with KMS Key Stored in AWS KWS (SSE-KMS)
- Leverage AWS Key Management Service to manage encryption keys
- Manager your own keys using AWS [[KMS (Key Management Service)]]
-  KMS advantages: user control + **audit key usage using [[CloudTrail]]**
- Header: "x-amz-server-side-encryption":"aws:kms"
- You have a default key already
- Automatically **rotates keys**.
- Only encrypts objects, not metadata
- You can have Single-Region keys and Multi-Region keys. They cannot be converted to each other, you would need to create a new bucket for that.


>[!INFO]
>Normally, when you encrypt files using KMS, it calls the API every single time, increasing cost.
>Instead, you can use **S3 Bucket Keys** to have a bucket-level encryption, decreasing cost.

##### Limitations
- If you use KMS, you may be impacted by KMS limits
- When you upload, it calls the **GenerateDataKey** KMS API, when you download, it calls the **Decrypt** KMS API. This counts towards the KMS quote per second
- You can increase quota using Service Quotas Console

---
**Use Server-Side Encryption with Amazon S3-Managed Keys (SSE-S3)** – Each object is encrypted with a unique key. As an additional safeguard, it encrypts the key itself with a master key that it regularly rotates. Amazon S3 server-side encryption uses one of the strongest block ciphers available, 256-bit Advanced Encryption Standard (AES-256), to encrypt your data.

**Use Server-Side Encryption with KMS Key Stored in AWS Key Management Service (SSE-KMS)** – Similar to SSE-S3, but with some additional benefits and charges for using this service. There are separate permissions for the use of a KMS key that provides added protection against unauthorized access of your objects in Amazon S3. SSE-KMS also provides you with an audit trail that shows when your KMS key was used and by whom. Additionally, you can create and manage customer-managed key or use AWS managed KMS keys that are unique to you, your service, and your Region.

---

#### SSE with Customer-Provided Keys (SSE-C)
- Manage your own keys
- AWS does **not** store the encryption key you provide. It is fully managed by customer
- HTTPS must be used, and keys should be provided in HTTP headers in every request


## Client-Side Encryption
- Uses client libraries such as Amazon S3 Client-Side Encryption Library
- Client must encrypt and decrypt data before sending and retrieving to Amazon S3

> DSSE-KMS is a new encryption method that is just "double encryption based on KMS"