### [[S3]] & Static Website
```
resource "aws_s3_bucket" "static_website" {
	bucket = "terraform}
```

#### Public Access Block
[Documentation]([aws_s3_bucket_public_access_block | Resources | hashicorp/aws | Terraform | Terraform Registry](https://registry.terraform.io/providers/hashicorp/aws/latest/docs/resources/s3_bucket_public_access_block))

```
resource "aws_s3_bucket_public_access_block" "static_website" {
  bucket                  = aws_s3_bucket.static_website.id
  block_public_acls       = false
  block_public_policy     = false
  ignore_public_acls      = false
  restrict_public_buckets = false
}
```

#### Public Read 
[Further Reading]([aws_s3_bucket_policy | Resources | hashicorp/aws | Terraform | Terraform Registry](https://registry.terraform.io/providers/hashicorp/aws/latest/docs/resources/s3_bucket_policy))
```
resource "aws_s3_bucket_policy" "static_website_public_read" {
  bucket = aws_s3_bucket.static_website.id



### This is optional, but since terraform is not sequential, if public access is not allowed before this public read, it might give an error.

	  depends_on = [
	    aws_s3_bucket_public_access_block.static_website
	  ]
	  
###
  policy = jsonencode({
    Version = "2012-10-17"
    Statement = [
      {
        Sid       = "PublicReadGetObject"
        Effect    = "Allow"
        Principal = "*"
        Action    = "s3:GetObject"
        Resource  = "${aws_s3_bucket.static_website.arn}/*"
      }
    ]
  })
}
```

#### Website Configuration
[Documentation]([aws_s3_bucket_website_configuration | Resources | hashicorp/aws | Terraform | Terraform Registry](https://registry.terraform.io/providers/hashicorp/aws/latest/docs/resources/s3_bucket_website_configuration))

```
resource "aws_s3_bucket_website_configuration" "static_website" {
  bucket = aws_s3_bucket.static_website.id

  index_document {
    suffix = "index.html"
  }

  error_document {
    key = "error.html"
  }
}
```

#### Upload Objects
[Documentation]([aws_s3_object | Resources | hashicorp/aws | Terraform | Terraform Registry](https://registry.terraform.io/providers/hashicorp/aws/latest/docs/resources/s3_object))


```
resource "aws_s3_object" "index_html" {
  bucket       = aws_s3_bucket.static_website.id
  key          = "index.html"
  source       = "build/index.html"
  etag         = filemd5("build/index.html")
  content_type = "text/html"
}

resource "aws_s3_object" "error_html" {
  bucket       = aws_s3_bucket.static_website.id
  key          = "error.html"
  source       = "build/error.html"
  etag         = filemd5("build/error.html")
  content_type = "text/html"
}
```

#### Expose Endpoint using Output

```
output "static_website_endpoint" {
  value = aws_s3_bucket_website_configuration.static_website.website_endpoint
}
```

You can run `terraform output` and it will output the FQDN of your S3 website.