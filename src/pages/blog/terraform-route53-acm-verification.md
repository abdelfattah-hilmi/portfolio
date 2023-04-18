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