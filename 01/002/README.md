# Use AWS Config to detect old access keys and disable them with SSM runbook

https://awstut.com/en/2023/05/20/use-aws-config-to-detect-old-access-keys-and-disable-them-with-ssm-runbook-en/

# Architecture

![soa-01-002-diagram](https://github.com/awstut-an-r/awstut-fa/assets/84276199/ffbeb863-3b1f-4402-86e1-b471b87d4a7d)

# Requirements

* AWS CLI
* S3 Bucket(Here, the bucket name is *my-bucket* and region is *ap-northeast-1*)

# Usage

## Tempalte File Modification

Modify the following locations in soa-01-002.yaml.

```yaml
Parameters:
  TemplateBucketName:
    Type: String
    Default: [bucket-name]
```

## Upload  Template Files to S3 Bucket

```bash
aws s3 cp . s3://my-bucket/soa-01-002/ --recursive
```

## CloudFormation Stack Creation

```bash
aws cloudformation create-stack \
--stack-name soa-01-002 \
--template-url https://my-bucket.s3.ap-northeast-1.amazonaws.com/soa-01-002/soa-01-002.yaml \
--capabilities CAPABILITY_IAM
```
