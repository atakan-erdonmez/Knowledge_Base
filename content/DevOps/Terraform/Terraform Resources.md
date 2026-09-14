Terraform takes dependencies into the consideration when creating resources. It does create [[IAM]] role before creating the [[EC2]] role if there is a dependency.

- Certain resources can be created in parallel, while others depend on each other must be created in a certain order.
- TF inspects expressions to automatically establish implicit dependencies between resources. Additionally, you can define explicit dependencies via the `depends_on` [[Terraform Meta-Arguments|meta-argument]].
- We can also force TF to replace a parent resource in case a child resource is modified by using the `replace_triggered_by` meta-argument (not common)