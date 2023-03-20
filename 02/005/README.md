# Periodically delete old AMIs – SSM Automation runbook version

https://awstut.com/en/2023/03/21/periodically-delete-old-amis-ssm-automation-runbook-version-en/

# Architecture

![soa-02-005-diagram](https://user-images.githubusercontent.com/84276199/226477215-275a82b8-3d8c-4254-83b2-530fc5bd71b8.png)

# Requirements

* AWS CLI
* S3 Bucket(Here, the bucket name is *my-bucket* and region is *ap-northeast-1*)

# Usage

## Tempalte File Modification

Modify the following locations in soa-02-005.yaml.

```yaml
Parameters:
  TemplateBucketName:
    Type: String
    Default: [bucket-name]
```

## Upload  Template Files to S3 Bucket

```bash
aws s3 cp . s3://my-bucket/soa-02-005/ --recursive
```

## CloudFormation Stack Creation

```bash
aws cloudformation create-stack \
--stack-name soa-02-005 \
--template-url https://my-bucket.s3.ap-northeast-1.amazonaws.com/soa-02-005/soa-02-005.yaml \
--capabilities CAPABILITY_IAM
```
