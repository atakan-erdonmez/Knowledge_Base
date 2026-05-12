

**Modules**: Codes that can be used to actions, like the AWS VPC module that lets you modify VPC
**Plugins**: Requirements for modules to work. Downloaded in the init

## Commands
- `terraform init`: Command to initialize the working dir that contains your code. Mandatory to run. It also setup the backend for storing state of the deployment.
- `terraform plan`: It reads the directory for your configs, and summarizes the plan to you. It doesn't deploy anything, just displays the overview of the deployment.
- `terraform apply`: Deploy the infrastructure. It can update the deployment or newly deploy.
- `terraform destroy`: Look at the state file and destroy all resources found in the state file.

**Flow**: Write IaC -> init -> plan -> apply -> destroy