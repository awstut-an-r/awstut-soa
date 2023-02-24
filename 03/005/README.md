# Create SSM Automation runbook to share AMI with another account using CloudFormation

https://awstut.com/en/2023/02/25/create-ssm-automation-runbook-to-share-ami-with-another-account-using-cloudformation-en/

# Architecture

![soa-03-005-diagram](https://user-images.githubusercontent.com/84276199/221305019-a37af979-9e2f-4990-92b3-424c6887c185.png)

# Requirements

* AWS CLI
* S3 Bucket(Here, the bucket name is *my-bucket* and region is *ap-northeast-1*)

# Usage

## Tempalte File Modification

Modify the following locations in soa-03-005.yaml.

```yaml
Parameters:
  TemplateBucketName:
    Type: String
    Default: [bucket-name]
```

## Upload  Template Files to S3 Bucket

```bash
aws s3 cp . s3://my-bucket/soa-03-005/ --recursive
```

## CloudFormation Stack Creation

```bash
aws cloudformation create-stack \
--stack-name soa-03-005 \
--template-url https://my-bucket.s3.ap-northeast-1.amazonaws.com/soa-03-005/soa-03-005.yaml \
--capabilities CAPABILITY_IAM
```
