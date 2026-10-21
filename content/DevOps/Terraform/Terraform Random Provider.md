```
terraform {
  required_version = "~> 1.7"
  required_providers {
    random = {
      source  = "hashicorp/random"
      version = "~> 3.0"
    }
  }
}
```


```
resource "random_id" "my_bucket_suffix" {
	byte_lenght = 4
}

resource "aws_s3_bucket" "static_website" {
	bucket = "projet-${random_id.my_bucket_suffix.hex}
	}
```