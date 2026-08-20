Variables are way of creating re-usable Terraform files. With variables, you can create small changes and make the terraform files environment or project independent.

[[Terraform Input Variable Types|Variable Types]]


You need 2 files:
- variables.tf(vars.tf): They define the variables, their types, descriptions etc
- terraform.tfvars: You define the values of variables here

### Example use case
provider.tf
```provider.tf
provider "aws" {
	access_key = "${var.AWS_ACCESS_KEY}"
	secret_key = "${var.AWS_SECRET_KEY}"
	region = "${var.AWS_REGION}"
}
```

variables.tf
```variables.tf
variable "AWS_ACCESS_KEY" {}
variable "AWS_SECRET_KEY" {}
variable "AWS_REGION" {
	default = "us-east-2"
}
```

terraform.tfvars
```terraform.tfvars
AWS_ACCESS_KEY = ""
AWS_SECRET_KEY = ""
AWS_REGION
```



Another variables.tf:
```variables.tf
variable "environment" {
	type = string
}

variable "location" {
	type = string
	default = "eastus"
	description = "The azure region to deploy resources"
	}
```


Alternatively, you can specify variables in command line while planning:
`terraform plan -var AWS_ACCESS_KEY="asdfasdlkjaue" -var AWS_SECRET_KEY="asdfkjkue"`
## Conditions
You can create specific conditions for the variables.
```variables.tf
variable "location" {
	type = string
	validation {
		condition = contains(["eastus","westus"],lower(var.location))
		error_message = "Unsupported Azure Region specified."
	}
}
```

## Input Variable Types
There are various data types for variables. It can be read [[Terraform Input Variable Types|here]]
