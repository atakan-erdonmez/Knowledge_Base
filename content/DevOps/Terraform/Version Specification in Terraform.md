---
created: 2026-05-14T11:29
updated: 2026-05-14T11:29
---
|**Syntax**|**Meaning**|**Why use it?**|
|---|---|---|
|`version = "6.45.0"`|**Exact.** Only use this version.|Best for production stability.|
|`version = "~> 6.45.0"`|**Pessimistic.** Allows `6.45.1`, `6.45.2`, but **not** `6.46.0`.|Best for getting security patches without breaking changes.|
|`version = ">= 6.45.0"`|**Minimum.** Anything newer than this is fine.|Good for shared modules where you want the latest features.|

```
terraform {
  required_providers {
    aws = {
      source  = "hashicorp/aws"
      # This tells Terraform: "Use exactly 6.45.0"
      version = "6.45.0" 
    }
  }
}

```