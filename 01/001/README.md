# Configure remediation actions when non-compliant resources are detected by AWS Config

https://awstut.com/en/2022/12/25/configure-remediation-actions-when-non-compliant-resources-are-detected-by-aws-config-en/

# Architecture

![soa-01-001-diagram](https://user-images.githubusercontent.com/84276199/209461983-b20ad43b-e146-4b4c-b1d7-dbd29cb13eec.png)

# Requirements

* AWS CLI
* S3 Bucket(Here, the bucket name is *my-bucket* and region is *ap-northeast-1*)

# Usage

## Tempalte File Modification

Modify the following locations in soa-01-001.yaml.

```yaml
Parameters:
  TemplateBucketName:
    Type: String
    Default: [bucket-name]
```

## Upload  Template Files to S3 Bucket

```bash
aws s3 cp . s3://my-bucket/soa-01-001/ --recursive
```

## CloudFormation Stack Creation

```bash
aws cloudformation create-stack \
--stack-name soa-01-001 \
--template-url https://my-bucket.s3.ap-northeast-1.amazonaws.com/soa-01-001/soa-01-001.yaml \
--capabilities CAPABILITY_IAM
```
