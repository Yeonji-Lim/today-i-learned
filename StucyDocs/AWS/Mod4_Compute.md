# 서비스 vs 리소스

## 서비스
EC2
Lambda
S3

## 리소스
EC2 instance
AMI
Lambda Function
S3 Bucket

### Amazon Resource Names (ARNs)
AWS 리소스 고유 식별

### Resource IDs
ARN 안에 들어감

### Resource Scope(level)
- Global : IAM, Route53, CloudFront, WAF, Shield
- Region : VPC, S3, DDB, CloudFormation, SNS, SQS, Lambda, API G/W, ECS, EKS
- AZ : EC2, EBS, RDS

# EC2 인스턴스

## Tag의 예
![](https://i.imgur.com/VeedHNv.png)

## AMI
EC2 인스턴스를 시작하는 데 필요한 모든 정보를 제공하는 템플릿 이미지
