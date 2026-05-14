---
tags:
  - "#terraform"
---


**Modules**: Codes that can be used to actions, like the AWS VPC module that lets you modify VPC
**Plugins**: Requirements for modules to work. Downloaded in the init

## Commands
- `terraform init`: Command to initialize the working dir that contains your code. Mandatory to run. It also setup the backend for storing state of the deployment. You also need to run it whenever you create a new file or directory.
- `terraform plan`: It reads the directory for your configs, and summarizes the plan to you. It doesn't deploy anything, just displays the overview of the deployment.
- `terraform apply`: Deploy the infrastructure. It can update the deployment or newly deploy.
- `terraform destroy`: Look at the state file and destroy all resources found in the state file.

**Flow**: Write IaC -> init -> plan -> apply -> destroy

## Providers
They are providers that allow TF to communicate with remote systems like cloud providers (AWS, GCP), SaaS providers (GitHub, Cloudflare), and even local infra (Docker, K8s).

Providers translates the HCL to specific API calls for systems to understand. As best practice, Providers should be versioned in your TF config files. TF finds and install Providers when you use `tf init`.

> Note: Using specific versions in your configs is best. Providers get regular updates, and an old config might not work with the latest release. If version is not specified, latest version is used.

More on [[Terraform Providers]]