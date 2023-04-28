# AWS WAF String Inspection – Headers/QueryString/Body/Cookies

https://awstut.com/en/2023/04/29/aws-waf-string-inspection-headers-querystring-body-cookies-en/

# Architecture

![soa-05-003-diagram](https://user-images.githubusercontent.com/84276199/235257953-5f6b3edf-42c8-4447-8f6b-5b9ef89e260f.png)

# Requirements

* AWS CLI
* S3 Bucket(Here, the bucket name is *my-bucket* and region is *ap-northeast-1*)

# Usage

## Tempalte File Modification

Modify the following locations in soa-05-003.yaml.

```yaml
Parameters:
  TemplateBucketName:
    Type: String
    Default: [bucket-name]
```

## Upload  Template Files to S3 Bucket

```bash
aws s3 cp . s3://my-bucket/soa-05-003/ --recursive
```

## CloudFormation Stack Creation

```bash
aws cloudformation create-stack \
--stack-name soa-05-003 \
--template-url https://my-bucket.s3.ap-northeast-1.amazonaws.com/soa-05-003/soa-05-003.yaml \
--capabilities CAPABILITY_IAM
```
