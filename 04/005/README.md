# Encrypting an RDS DB instance – Step Functions version

https://awstut.com/en/2023/09/09/encrypting-an-rds-db-instance-step-functions-version-en/

# Architecture

![soa-04-005-diagram](https://github.com/awstut-an-r/awstut-fa/assets/84276199/77c7d6a8-bcd7-453b-83dd-eb112dbbe02e)

# Requirements

* AWS CLI
* S3 Bucket(Here, the bucket name is *my-bucket* and region is *ap-northeast-1*)

# Usage

## Tempalte File Modification

Modify the following locations in soa-04-005.yaml.

```yaml
Parameters:
  TemplateBucketName:
    Type: String
    Default: [bucket-name]
```

## Upload  Template Files to S3 Bucket

```bash
aws s3 cp . s3://my-bucket/soa-04-005/ --recursive
```

## CloudFormation Stack Creation

```bash
aws cloudformation create-stack \
--stack-name soa-04-005 \
--template-url https://my-bucket.s3.ap-northeast-1.amazonaws.com/soa-04-005/soa-04-005.yaml \
--capabilities CAPABILITY_IAM
```
