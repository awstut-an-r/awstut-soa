# Periodically delete old AMIs – Step Functions version

https://awstut.com/en/2023/03/20/periodically-delete-old-amis-step-functions-version-en/

# Architecture

![soa-02-004-diagram](https://user-images.githubusercontent.com/84276199/226213641-8f4c6006-241d-438c-b761-b4dde100cd40.png)

# Requirements

* AWS CLI
* S3 Bucket(Here, the bucket name is *my-bucket* and region is *ap-northeast-1*)

# Usage

## Tempalte File Modification

Modify the following locations in soa-02-004.yaml.

```yaml
Parameters:
  TemplateBucketName:
    Type: String
    Default: [bucket-name]
```

## Upload  Template Files to S3 Bucket

```bash
aws s3 cp . s3://my-bucket/soa-02-004/ --recursive
```

## CloudFormation Stack Creation

```bash
aws cloudformation create-stack \
--stack-name soa-02-004 \
--template-url https://my-bucket.s3.ap-northeast-1.amazonaws.com/soa-02-004/soa-02-004.yaml \
--capabilities CAPABILITY_IAM
```
