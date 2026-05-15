---
tags:
  - "#terraform"
created: 2026-05-14T11:00
updated: 2026-05-14T11:43
---
[[Terraform Basics#Providers]]

In order to install providers, create the directory `providers/`, and put a `providers.tf` file in it.

Then, put providers like this:

```terraform
# 1. THE ENGINE ROOM (Dependency Management)
terraform {
  required_version = ">= 1.10.0"
  
  required_providers {
    aws = {
      source  = "hashicorp/aws"
      version = "6.45.0" # Exactly the version you wanted
    }
    azurerm = {
      source  = "hashicorp/azurerm"
      version = "4.72.0"
    }
  }
}

# 2. THE CONNECTION (Authentication & Region)
provider "aws" {
  region = "eu-central-1"
  # Note: No keys here! It uses your 'aws login' session automatically.
}

provider "azurerm" {
  features {} # This block is mandatory for the Azure provider to work
}
```

Then, you can run `terraform init` to update and install providers.

## Best Practice
When you run terraform, it collects every .tf file in the directory, merges them, and treat them like a big file. So, you should try not to repeat same info everywhere.

The `terraform {}` block is the actual engine, which you should define in `providers.tf` or something similar. It should include terraform block as well as individual providers

Then, when you are creating job-files (REPLACE HERE WITH ACTUAL NAME), you should not specify any provider or terraform block