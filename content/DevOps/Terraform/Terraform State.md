---
tags:
  - terraform
---
It is a file that contains the current state of the Terraform deployment. It is a critical file for Terraform to work.

- It is a stored flat file named `terraform.tfstate`
- It is stored in the working directory, but can be stored remotely
- It helps to calculate deployment delta (changes in deployments)

> Terraform State files can be huge, tens of thousands of lines, so it is not a useful file to look into.

- State is always required in Terraform.
- **Important!** The state contains extremely sensitive data, so be careful regarding who has access to it.
- The state file also stores metadata, such as resource dependencies, so that Terraform knows in which order resources must be created, updated or deleted.
- Before any planning operation, Terraform refreshes the state with the information from the respective real-world objects.
    - This is essential to avoid configuration drift. If a real-world object has been modified outside of Terraform and the respective configuration has not been updated, Terraform will revert the changes.
- State can be either stored locally (default) or in several remote backends (S3, Google Cloud Storage, Terraform Cloud, among others).
- **State locking:** locks the state while executing write operations to prevent concurrent modifications and state corruption.

### State Backup
`terraform.tfstate.backup` file holds the previous state of the infrastructure. It is not commonly used, generally [[Git]] or [[S3#Versioning|S3 Versioning]] is used