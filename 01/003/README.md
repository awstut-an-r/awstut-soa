# CloudWatch metrics streams to deliver metrics to S3 buckets

https://awstut.com/en/2024/05/12/cloudwatch-metrics-streams-to-deliver-metrics-to-s3-buckets-en/

# Architecture

![soa-01-003-diagram](https://github.com/awstut-an-r/awstut-fa/assets/84276199/e552e9d5-4a8f-49a0-b5a6-124de3f1c39a)

# Requirements

* AWS CLI
* S3 Bucket(Here, the bucket name is *my-bucket* and region is *ap-northeast-1*)

# Usage

## Tempalte File Modification

Modify the following locations in soa-01-003.yaml.

```yaml
Parameters:
  TemplateBucketName:
    Type: String
    Default: [bucket-name]
```

## Upload  Template Files to S3 Bucket

```bash
aws s3 cp . s3://my-bucket/soa-01-003/ --recursive
```

## CloudFormation Stack Creation

```bash
aws cloudformation create-stack \
--stack-name soa-01-003 \
--template-url https://my-bucket.s3.ap-northeast-1.amazonaws.com/soa-01-003/soa-01-003.yaml \
--capabilities CAPABILITY_IAM
```
