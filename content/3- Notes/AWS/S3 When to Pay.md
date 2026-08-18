---
link:
  - "[[S3]]"
---

| **Scenario / Traffic Flow**                                 | **Cost Status** | **Cost Details**                                                                                                              |
| ----------------------------------------------------------- | --------------- | ----------------------------------------------------------------------------------------------------------------------------- |
| **Uploading from the Internet**                             | **FREE**        | $0.00 per GB inbound                                                                                                          |
| **Transferring within the Same Region** (Inter-AZ/Intra-AZ) | **FREE**        | $0.00 via S3 public endpoints or **VPC Gateway Endpoints**                                                                    |
| **Sending Data to CloudFront CDN**                          | **FREE**        | $0.00 for data transfer from S3 to CloudFront                                                                                 |
| **Downloading to the Internet**                             | **PAID**        | ~$0.09 per GB (after the initial 100 GB global free tier)                                                                     |
| **Cross-Region Transfers**                                  | **PAID**        | ~$0.02 per GB when moving data to a different AWS Region                                                                      |
| **Traffic passing through a NAT Gateway**                   | **PAID**        | ~$0.045 per GB processing fee if a private EC2 instance routes S3 traffic through a NAT Gateway instead of a Gateway Endpoint |
