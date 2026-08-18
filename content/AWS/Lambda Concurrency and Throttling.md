---
link:
  - "[[Lambda]]"
---
## Concurrency and Throttling
Concurrency limit is 1000 concurrent executions. You can set a "reserved concurrency" (limit) at the function to level to limit this, and it is recommended. This limit applies to all your functions in your account.

Each invocation over the concurrency limit will trigger a "Throttle"

**Cold Start** The initialization delay that occurs when AWS downloads your code and starts a runtime for a new execution environment. This typically happens during the first request after a period of inactivity or when the function scales out to handle more traffic.

**Unreserved Concurrency** The default pool of capacity shared by all functions in an AWS account within a specific region. It allows for flexible scaling, but functions compete for the same resources, meaning a spike in one function can potentially throttle others.

**Reserved Concurrency** A specific amount of capacity set aside for a single function to guarantee it always has execution environments available. It also acts as a hard limit, preventing that function from scaling beyond a certain point and overwhelming downstream resources like databases.

**Provisioned Concurrency** Pre-warmed execution environments that stay initialized and ready to respond immediately to traffic. This feature eliminates cold start latency for the specified capacity in exchange for a consistent hourly cost.

