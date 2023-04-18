---
title: "Aws acm dns verification using route53 and terraform"
excerpt: "Aws acm dns verification using route53 and terraform"
publishDate: "2023-04-18T19:58:36.050Z"
image: "https://www.datocms-assets.com/2885/1620155439-blog-library-product-terraform-aws-logomarks.jpg"
category: "Guides"
author: "Abdelfattah Hilmi"
layout: "@layouts/BlogLayout.astro"
tags: [Cloud, Devops, SRE,Terraform]
---

## Certficate Quotas:
- Default quota: 2500, Expired and revoked certificates continue to count toward this total
- You can request up to twice your quota of ACM certificates per year, region, and account.
- You can only have 2,500 certificates at any given time.
- The default quota is 10 **domain names** for each ACM certificate

## Set up terraform environment for dev:
### First- setup creds:

- to avoid specifying the creds in your main.tf it is better to use env variables

```bash
export  AWS_ACCESS_KEY_ID="ur access key ID"
export AWS_SECRET_ACCESS_KEY="ur access secret"
```
- In "main.tf" declare you provider and set it up: the access is done through env vars so we only need to specify the region

```hcl
terraform {
  required_providers {
    aws = {
      source  = "hashicorp/aws"
      version = "~>4.16"
    }
  }
  required_version = ">= 1.2.0"
}

provider "aws" {
  region = "eu-west-2"
}
```

## How to create a route53 record:

- In order to create a route in a previously created hosted zone, we first import the hosted zone using the data block then we create a route using the imported zone id:
```hcl
#adding a record to existing hosted zone

data "aws_route53_zone" "hosted_zone" {
  name = var.domain_name
}


resource "aws_route53_record" "site_domain" {
  zone_id = data.aws_route53_zone.hosted_zone.zone_id
  name    = var.record_name
  type    = "A" # specify any record type 
  ttl     = 300
  records = ["valid ipv4 address because the type is `A` record"]
}
```
- note that the "domain name" and "record name" are imported from the variables file 'vars.tf' and they are declared as the following:

```hcl
variable "domain_name" {
  default     = "{your domain name}"
  description = "domain name variable"
  type        = string
}
variable "record_name" {
  default     = "{your record name}"
  description = "record name variable"
  type        = string
}
``` 

## Request certificates and validate them using DNS in route53:

- Upon requesting your certificate the DNS verification requires that you add some CNAME records to your route53 domaine name:
- therefore the steps we should follow are:
  - Getting the route53 zone using data block
  - Requesting/Creating a public certificate 
  - Creating the CNAME records created after requesting the certificate
  - Creating the aws_certification_validation ressource

the hcl code is the following:
```hcl
# get the data about route53 zone 
data "aws_route53_zone" "route53_zone" {
  name         = "abdelhilmi.com"
  private_zone = false
}

#Request a certificate for our domain name from ACM and validate it using dns in route53
resource "aws_acm_certificate" "acm_certificate" {
  domain_name               = var.main_subdomain
  subject_alternative_names = var.subdomain_alternatives
  validation_method         = "DNS"

  lifecycle {
    create_before_destroy = true
  }
}

resource "aws_route53_record" "route53_record" {
  for_each = {
    for dvo in aws_acm_certificate.acm_certificate.domain_validation_options : dvo.domain_name => {
      name   = dvo.resource_record_name
      record = dvo.resource_record_value
      type   = dvo.resource_record_type
    }
  }

  allow_overwrite = true
  name            = each.value.name
  records         = [each.value.record]
  ttl             = 60
  type            = each.value.type
  zone_id         = data.aws_route53_zone.route53_zone.zone_id
}

resource "aws_acm_certificate_validation" "acm_certificate_validation" {
  certificate_arn         = aws_acm_certificate.acm_certificate.arn
  validation_record_fqdns = [for record in aws_route53_record.route53_record : record.fqdn]
}

```

- add the previous block under your provider config in "main.tf" and run :

```shell
foo@bar:~$ terraform fmt
foo@bar:~$ terraform validate 
foo@bar:~$ terraform apply

#delete everything created
foo@bar:~$ terraform destroy
```