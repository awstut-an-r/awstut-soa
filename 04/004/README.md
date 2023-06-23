# Use S3 bucket policy to allow or deny access on an address basis – aws:SourceIp

https://awstut.com/en/2023/06/24/use-s3-bucket-policy-to-allow-or-deny-access-on-an-address-basis-awssourceip-en/

# Architecture

![soa-04-004-diagram](https://github.com/awstut-an-r/awstut-fa/assets/84276199/14e497f8-d06d-4a43-bc5b-1c704afbe815)

# Requirements

* AWS CLI
* S3 Bucket(Here, the bucket name is *my-bucket* and region is *ap-northeast-1*)

# Usage

## Tempalte File Modification

Modify the following locations in soa-04-004.yaml.

```yaml
Parameters:
  TemplateBucketName:
    Type: String
    Default: [bucket-name]
```

## Upload  Template Files to S3 Bucket

```bash
aws s3 cp . s3://my-bucket/soa-04-004/ --recursive
```

## CloudFormation Stack Creation

```bash
aws cloudformation create-stack \
--stack-name soa-04-004 \
--template-url https://my-bucket.s3.ap-northeast-1.amazonaws.com/soa-04-004/soa-04-004.yaml \
--capabilities CAPABILITY_IAM
```
