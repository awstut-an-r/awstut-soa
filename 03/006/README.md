# Automatically tag provisioned products using AWS Service Catalog TagOption Library

https://awstut.com/en/2023/04/09/automatically-tag-provisioned-products-using-aws-service-catalog-tagoption-library-en/

# Architecture

![soa-03-006-diagram](https://user-images.githubusercontent.com/84276199/230763974-81dbc2bb-1df1-4e5f-bd99-747ebc6d9136.png)

# Requirements

* AWS CLI
* S3 Bucket(Here, the bucket name is *my-bucket* and region is *ap-northeast-1*)

# Usage

## Tempalte File Modification

Modify the following locations in soa-03-006.yaml.

```yaml
Parameters:
  TemplateBucketName:
    Type: String
    Default: [bucket-name]
```

## Upload  Template Files to S3 Bucket

```bash
aws s3 cp . s3://my-bucket/soa-03-006/ --recursive
```

## CloudFormation Stack Creation

```bash
aws cloudformation create-stack \
--stack-name soa-03-006 \
--template-url https://my-bucket.s3.ap-northeast-1.amazonaws.com/soa-03-006/soa-03-006.yaml \
--capabilities CAPABILITY_IAM
```
