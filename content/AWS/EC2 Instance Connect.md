---
link:
  - "[[EC2]]"
---
  
Amazon EC2 Instance Connect provides a secure and auditable way to establish **temporary SSH** sessions to EC2 instances **by injecting a one-time-use public key into the instance** at connection time. 

When used **without Session Manager**, EC2 Instance Connect requires the instance to have a **public IP** address, and connections are made **over the internet** via the public IP. This setup is ideal for temporary administrative access to public instances without the need to distribute or manage long-term SSH key pairs. The session is short-lived, and logs are available via CloudTrail for auditing purposes.