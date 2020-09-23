# SSL Proxy for AWS EC2 based website

## What is it?
It is a Serverless Framework based AWS CloudFormation template to create SSL Proxy for AWS EC2 based website.

## What is being deployed
1. S3 bucket to redirect to the domain with www prefix
2. CloudFront distribution pointing to the S3 bucket
3. CloudFront distribution pointing to EC2 instance with the website

DNS, EC2 instances and SSL certificate are not being managed with this stack because it may be a good idea to store them in separate stacks.

## Usage
Copy config/parameters.json to .apprc.
```
{
  "domain": "RENAME_ME",
  "sslCertificateARN": "RENAME_ME",
  "EC2InstanceAddress": "RENAME_ME",
  "aws": {
    "serviceId": "RENAME_ME",
    "region": "eu-central-1",
    "stage": "prod"
  }
}
```
Change RENAME_ME values to the appropriate ones.
* domain is the website address without www prefix
* sslCertificateARN is ARN of SSL certificate created beforehand in CertificateManager
* EC2InstanceAddress is Public IPv4 DNS of the EC2 instance running your website
* serviceId is any string which complies with CloudFormation stack naming requirements
Run sls-deploy.
