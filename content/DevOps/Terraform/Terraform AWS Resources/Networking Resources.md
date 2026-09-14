**Link**: [[AWS]]
### [[VPC]]
```
resource "aws_vpc" "main" {
  cidr_block = "10.0.0.0/16"
  
  tags = {
	  Name = "Main-VPC" # the display name in AWS
	  ManagedBy = "Terraform"
  }
}
```

#### subnet
```
resource "aws_subnet" "public" {
    vpc_id = aws_vpc.mainvpc.id
    cidr_block = "10.0.1.0/24"
}
```

> Note: When specifying `vpc_id`, you need to add the `.id` to the end of the VPC name. If you just say `aws_vpc_mainvpc`, it refers to the *entire object* instead of just the ID.