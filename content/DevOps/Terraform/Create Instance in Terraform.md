```
resource "aws_instance" "example" {
  ami           = "ami-01007d47228a6f3a3" # Standard Amazon Linux 2023 for eu-central-1
  instance_type = "t3.micro"
  count = 3 # For specifying count

  tags = {
    Name = "Atakan-Test-Instance-${count.index}" # this will append count-number
  }
}
```

Check [[Terraform Providers#Best Practice]] to understand the structure. You should not put terraform or providers block in the individual work-files. They should stay central somewhere else.

Then, you should run [[Terraform Basics#Commands|terraform init]] for the file to be available.