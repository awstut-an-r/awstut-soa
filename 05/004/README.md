# Route53 latency-based routing for ALB

https://awstut.com/en/2023/11/11/route53-latency-based-routing-for-alb-en/

# Architecture

![soa-05-004-diagram](https://github.com/awstut-an-r/awstut-fa/assets/84276199/31296734-63a1-4d06-b26f-466b0199996b)

# Requirements

* AWS CLI
* S3 Bucket(Here, the bucket name is *my-bucket* and region is *ap-northeast-1*)

# Usage

## Tempalte File Modification

Modify the following locations in soa-05-004.yaml.

```yaml
Parameters:
  TemplateBucketName:
    Type: String
    Default: [bucket-name]

  DomainName:
    Type: String
    Default: [domain-name]
    
  HostedZoneId:
    Type: String
    Default: [hosted-zone-id]
```

## Upload  Template Files to S3 Bucket

```bash
aws s3 cp . s3://my-bucket/soa-05-004/ --recursive
```

## CloudFormation Stack Creation

```bash
aws cloudformation create-stack \
--stack-name soa-05-004 \
--template-url https://my-bucket.s3.ap-northeast-1.amazonaws.com/soa-05-004/soa-05-004.yaml \
--capabilities CAPABILITY_NAMED_IAM
```
