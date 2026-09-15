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

#### Subnet
```
resource "aws_subnet" "public" {
    vpc_id = aws_vpc.mainvpc.id
    cidr_block = "10.0.1.0/24"
}
```

> Note: When specifying `vpc_id`, you need to add the `.id` to the end of the VPC name. If you just say `aws_vpc_mainvpc`, it refers to the *entire object* instead of just the ID.


#### IGW
```terraform
resource "aws_internet_gateway" "main" {
    vpc_id = aws_vpc.mainvpc.id
    
    tags = {
        ManagedBy = "Terraform"
    }
}
```

#### Route Table & Association
```
resource "aws_route_table" "public_rt"{
    vpc_id = aws_vpc.mainvpc.id

    route {
        cidr_block =  = "0.0.0.0/0"
        gateway_id = aws_internet_gateway.main.id
    }
}

resource "aws_route_table_association" "public" {
    subnet_id = aws_subnet.public.id
    route_table_id = aws_route_table.public_rt.id
}
```

