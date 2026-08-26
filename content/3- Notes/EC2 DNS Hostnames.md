
When you launch an [[EC2]] instance into a default [[VPC]], AWS provides it with public and private DNS hostnames that correspond to the public IPv4 and private IPv4 addresses for the instance.

You don't need [[Route 53]] for a public hostname.


However, when you launch an instance into a non-default VPC, AWS provides the instance with a private DNS hostname only. New instances will only be provided with a public DNS hostname depending on these two DNS attributes: the **DNS resolution** and **DNS hostnames** that you have specified for your VPC and if your instance has a public IPv4 address.