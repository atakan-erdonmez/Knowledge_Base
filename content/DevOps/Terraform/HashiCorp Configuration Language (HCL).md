**Link:** [[Terraform]]


## Terraform Block
Main block, used to configure project-level variables like required providers, backend, and required versions.

- Only constants are allowed, inputs variables or resource references are not allowed.
- `cloud` block: Used to configure [[Terraform Cloud]]
- `backend` block: Used to configure a state backend for the project
- `required version` key: Specifies accepted versions of Terraform for the current project
- `required providers` block: Specifies the required providers for the current project or module, with version
```
terraform {
	required_version = "1.7.0" 
	
	backend "s3" { 
	//
	}
  required_providers {
    aws = {
      source  = "hashicorp/aws"
      version = "~> 5.0"
    }
  }
}
```
> You can use [[Terraform Random Provider|Random]] provider for creating a random sequence of text.



#### Version Constraints

| Symbol       | Meaning                                      |
| ------------ | -------------------------------------------- |
| =            | Allows only specified version                |
| !=           | Excludes an exact version                    |
| >=, <=, >, < | Comparison                                   |
| ~>           | Allows only the rightmost digit to increment |
**Examples**:
- required_version = ">-1.7.0"
- required_version = ">1.5.0, <1.7.0" 
- required_version = "~>1.5.0"
- required_version = "~>1.5"

## Resource
The individual resource that will be managed via Terraform
```
resource "aws_s3_bucket" "my_bucket" {
  bucket = var.bucket_name
}
```

- **Data**: A resource that is outside of our management. A resource that will be used as a data source
```
data "aws_s3_bucket" "my_external_bucket" {
  bucket = "not-managed-by-us"
}
```

- **Variable**: A variable name that will be used in the config
```
variable "bucket_name" {
  type        = string
  description = "My variable used to set bucket name"
  default     = "my_default_bucket_name"
}
```

- **Output**: To expose information about our configuration
```
output "bucket_id" {
  value = aws_s3_bucket.my_bucket.id
}
```

- **Locals**: Local variable, temporary variables. Variables that you create inside a function, but that doesn't return any value or used in as a parameter
```
locals {
  local_example = "This is a local variable"
}
```

- **Modules**: Reusable codes that is defined somewhere in the project directory
```
module "my_module" {
  source = "./module-example"
}
```


## Providers
Providers block specifies provider parameters, like region
```
provider "aws" {
  region = "eu-central-1"
}
```