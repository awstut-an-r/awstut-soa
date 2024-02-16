# Use S3 lifecycle rules to change the class of objects

https://awstut.com/en/2024/02/17/use-s3-lifecycle-rules-to-change-the-class-of-objects-en/

# Architecture

![soa-06-001-diagram](https://github.com/awstut-an-r/awstut-fa/assets/84276199/a849a1ad-53f1-48f8-ad6b-ddb62f8bca5e)

# Requirements

* AWS CLI
* S3 Bucket(Here, the bucket name is *my-bucket* and region is *ap-northeast-1*)

# Usage

## Tempalte File Modification

Modify the following locations in soa-06-001.yaml.

```yaml
Parameters:
  TemplateBucketName:
    Type: String
    Default: [bucket-name]
```

## Upload  Template Files to S3 Bucket

```bash
aws s3 cp . s3://my-bucket/soa-06-001/ --recursive
```

## CloudFormation Stack Creation

```bash
aws cloudformation create-stack \
--stack-name soa-06-001 \
--template-url https://my-bucket.s3.ap-northeast-1.amazonaws.com/soa-06-001/soa-06-001.yaml \
--capabilities CAPABILITY_NAMED_IAM
```
