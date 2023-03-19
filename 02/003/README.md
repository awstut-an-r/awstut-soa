# Introduction to Data Lifecycle Manager – Create EBS Snapshot/AMI periodically

https://awstut.com/en/2023/03/19/introduction-to-data-lifecycle-manager-create-ebs-snapshot-ami-periodically-en/

# Architecture

![soa-02-003-diagram](https://user-images.githubusercontent.com/84276199/226166043-cd598ed0-f538-4177-9677-46e28e86cea5.png)

# Requirements

* AWS CLI
* S3 Bucket(Here, the bucket name is *my-bucket* and region is *ap-northeast-1*)

# Usage

## Tempalte File Modification

Modify the following locations in soa-02-003.yaml.

```yaml
Parameters:
  TemplateBucketName:
    Type: String
    Default: [bucket-name]
```

## Upload  Template Files to S3 Bucket

```bash
aws s3 cp . s3://my-bucket/soa-02-003/ --recursive
```

## CloudFormation Stack Creation

```bash
aws cloudformation create-stack \
--stack-name soa-02-003 \
--template-url https://my-bucket.s3.ap-northeast-1.amazonaws.com/soa-02-003/soa-02-003.yaml \
--capabilities CAPABILITY_IAM
```
