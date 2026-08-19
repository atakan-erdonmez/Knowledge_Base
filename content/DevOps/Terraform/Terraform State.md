---
tags:
  - terraform
---
It is a file that contains the current state of the Terraform deployment. It is a critical file for Terraform to work.

- It is a stored flat file named `terraform.tfstate`
- It is stored in the working directory, but can be stored remotely
- It helps to calculate deployment delta (changes in deployments)