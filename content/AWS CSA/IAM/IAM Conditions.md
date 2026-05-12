#### aws:SourceIP
Restrict client IP that make API calls

#### aws:RequestedRegion
Restrict the region the API calls are made to

#### ec2:ResourceTags
If the EC2 instance has this tags, then allow

#### aws:MultiFactorAuthPresent
Check if MFA is enabled 

#### s3:ListBucket
This permission type only applies to specific buckets => bucket-level permission
arn:aws:s3:::test

#### s3:GetObject, s3:PutObject, s3:DeleteObject
Applies to arn:aws:s3:::test/*
Object-level permission

#### aws:PrincipalOrgID
Access to specific members of AWS Organization