### On-Demand Instances

On-Demand is the default, most flexible, and highest-cost pricing model for EC2. You launch virtual servers at a fixed hourly or per-second rate with zero upfront costs, long-term contracts, or commitment policies. It is designed for short-term, unpredictable, or spike-heavy workloads that cannot be interrupted, or for applications being tested before moving to a commitment model.

### Reserved Instances (RIs)

Reserved Instances are a discount mechanism where you commit to a specific instance configuration (family, size, region, OS, tenancy) for a **1-year or 3-year term** in exchange for savings up to 72% over On-Demand rates. **Standard RIs** are rigid but offer the deepest discounts, while **Convertible RIs** allow you to change instance attributes during the term if the new configuration is of equal or greater value. **Zonal RIs** offer a physical capacity reservation in a specific Availability Zone, whereas **Regional RIs** offer broader billing optimization across an entire region without capacity guarantees.

You can  sell Standard RIs in Reserved Instance Marketplace.
### Savings Plans

Savings Plans are a modern, highly flexible commitment model that reduces your AWS bill when you pledge to spend a consistent **monetary amount per hour** (e.g., $10/hour) for a 1-year or 3-year term. Unlike RIs, which tie you to specific infrastructure attributes, Savings Plans automatically apply discounts across changing instance families, sizes, operating systems, regions, and even shift seamlessly between EC2, AWS Fargate, and AWS Lambda when utilizing a _Compute Savings Plan_. They offer up to 72% savings, matching the financial benefits of RIs but vastly simplifying ongoing management across elastic or evolving modern architectures.

### Spot Instances

Spot Instances allow you to purchase spare, unused AWS EC2 capacity at steep discounts of **up to 90% off** On-Demand pricing. The core trade-off is that Spot instances are fully interruptible; if AWS needs the capacity back for On-Demand or Reserved customers, your instance will be terminated, stopped, or hibernated with only a **2-minute warning notification**. They are ideal for fault-tolerant, stateless, or batch-processing applications that can easily resume or scale down without impacting the user experience.

### Spot Fleet

A Spot Fleet is a collection or collection framework of Spot Instances (and optionally On-Demand instances) wrapped into a single management layer to meet a "target capacity" you define. Instead of requesting a single instance type, you define multiple acceptable instance families and Availability Zones in a launch template, allowing the fleet manager to automatically provision the cheapest or most stable combination of available spare capacity. Spot Fleets automatically attempt to replace terminated instances to maintain your target capacity, offering a resilient way to handle Spot infrastructure at scale.

### Dedicated Instances

Dedicated Instances are standard EC2 instances that run inside a Virtual Private Cloud (VPC) on physical hardware exclusively allocated to a single AWS customer account. They provide physical isolation from multi-tenant "noisy neighbors" at the hypervisor level to satisfy corporate data isolation requirements or compliance rules, but they abstract away all hardware visibility. You pay for these instances on a per-instance hourly basis, alongside a flat structural "Dedicated Region Fee" (approximately $2/hour per region) regardless of how many Dedicated Instances you deploy.

### Dedicated Hosts

Dedicated Hosts give you full ownership, visibility, and physical allocation of an entire bare-metal server in an AWS data center. Unlike Dedicated Instances, you can view the physical socket count, core count, and specific Host IDs, which is necessary for **Bring Your Own License (BYOL)** scenarios involving strict enterprise software (like Microsoft SQL Server or Oracle) that requires physical core tracking. You are billed based on the entire host footprint regardless of how many instances you actively run on it, and it features advanced controls like _Host Affinity_ to ensure an instance always boots back onto the exact same physical chassis.

## Technical Comparisons

### 1. Financial Commitment Models

This table contrasts models designed to lower baseline costs against the standard on-demand rate.

|**Feature**|**On-Demand Instances**|**Reserved Instances (RIs)**|**Savings Plans (SPs)**|
|---|---|---|---|
|**Commitment Basis**|None (Pay-as-you-go)|Specific Infrastructure Attributes|Dollar-per-hour spend ($/hr)|
|**Term Duration**|None|1 or 3 Years|1 or 3 Years|
|**Max Saving Potential**|Baseline (0% Discount)|Up to 72%|Up to 72%|
|**Capacity Guarantee**|No|Optional (Only with Zonal RIs)|No|
|**Fargate/Lambda Coverage**|No|No|Yes (Compute Savings Plan)|
|**Change Flexibility**|Instant modification|Limited (Requires Convertible RI)|Automatic across attributes|

### 2. Spot Management Frameworks

This table defines how independent spot instances differ from managed fleets.

|**Feature**|**Spot Instances**|**Spot Fleet**|
|---|---|---|
|**Management Unit**|Single Instance|Collection of Instances (Fleet)|
|**On-Demand Blending**|No|Yes (Can mix Spot and On-Demand)|
|**Target Allocation Strategy**|Manual selection|Automated (Capacity-optimized, lowest price)|
|**Interruption Behavior**|Terminates/stops target instance|Automatically provisions replacements|
|**Configuration Input**|Single instance type request|Multiple instance types via Launch Template|

### 3. Single-Tenant Hardware Options

This table highlights the difference between software isolation and hardware-level management.

|**Feature**|**Dedicated Instances**|**Dedicated Hosts**|
|---|---|---|
|**Physical Isolation**|Yes (Single AWS Account per Host)|Yes (Single AWS Account per Host)|
|**Hardware Visibility**|Hidden (No core/socket metrics)|Full (Sockets, cores, physical Host ID)|
|**Billing Mechanism**|Per-instance hourly fee + Region Fee|Flat per-host fee (Regardless of utilization)|
|**BYOL Core Compliance**|Limited support|Full support (Required for per-core licenses)|
|**Instance Placement Control**|Handled automatically by AWS|Manual placement or Host Affinity control|
|**Instance Size Mixing**|N/A (Standard instance allocation)|Yes (Mix sizes within same instance family)|