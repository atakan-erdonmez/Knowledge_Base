### [[EC2]]
```
resource "aws_instance" "web" {
    ami = "ami-06a6b712245f1f681"
    associate_public_ip_address = true
    instance_type = "t3.micro"
    subnet_id = aws_subnet.public.id
    vpc_security_group_ids = [aws_security_group.public_http_traffic.id] # attach security group
}

```

#### User Data
```
# inside ec2 resource
user_data = <<-EOF
						#!/bin/bash
						apt-get update -y
						...
						EOF

```

> User data normally only runs when creating the instance, not when restarting. So, if you change it and run `terraform apply`, it won't have an affect. To solve:

1. You can add `user_data_replace_on_change = true` parameter, which recreates the EC2 instance
2. You can use `terraform destroy` and recreate
3. You can use `-replace="aws_instance.my_web_instance` flag, which will recreate the instance specified in the flag, applying the user data script
#### Security Group
```
resource "aws_security_group" "public_http_traffic" {
    description = "Enable 80 & 443"
    name = "public-http-traffic"
    vpc_id = aws_vpc.mainvpc.id
}

resource "aws_vpc_security_group_ingress_rule" "http" {
    security_group_id = aws_security_group.public_http_traffic.id
    cidr_ipv4 = "0.0.0.0/24"
    from_port = 80
    to_port = 80
    ip_protocol = "tcp"
}

resource "aws_vpc_security_group_ingress_rule" "https" {
    security_group_id = aws_security_group.public_http_traffic.id
    cidr_ipv4 = "0.0.0.0/24"
    from_port = 443
    to_port = 443
    ip_protocol = "tcp"
}

resource "aws_vpc_security_group_egress_rule" "all" {
    security_group_id = aws_security_group.public_http_traffic.id
    cidr_ipv4 = "0.0.0.0/0"
    ip_protocol = "-1" # any IP, any port
}
```

