In the `providers.tf`, you can specify a backend.

By default, local storage will be used as the backend. You can specify either Terraform Cloud or a third-party backend, like [[S3]].

```providers.tf
terraform {
....

backend "s3" {
  bucket = "<your-bucket-name>"
  key    = "04-backends/state.tfstate" # name&prefix of the file in S3
  region = "<your-aws-region>"
}

}
```

In order to have a backend, you need to create the infrastructure, but in order to create an infrastructure, you need a backend. There are solutions to this.



### S3 State Locking with DynamoDB
S3 supports state locking, and it uses [[DynamoDB]]. You should add the line `dynamodb_table = 'my-dynamodb-table` to the backend block.

It is needed for state locking with S3.


### Partial Backend
You can create a separate/multiple backend file (e.g. `dev.s3.tfbackend`), put the content of the backend, then specify it using `terraform init -backend-config=dev.s3.tfbackend`. 
- You might need to use `-migrate-state` flag

```dev.s3.tfbackend
bucket = "my-bucket"
key = "backends/dev'state.tfstate"
region = "us-east-1"
```