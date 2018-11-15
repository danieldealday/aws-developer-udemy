# Serverless Application Model (SAM)
- an extension to CloudFormation used to define serverless applications
- simplified syntax for defining serverless resrouces: APIs, Lambda Functions, DynamoDB tables etc.
- use the SAM CLI to package you deployment code, upload it to S3 and deploy your serverless application

## SAM CLI Commands
- `sam package` - zip you code artifacts, upload to S3 and produce a SAM file using AWS CloudFormation
  - template file: `./mytemplate.yml`
  - output template file: `sam-template.yml`
  - s3-bucket: `s3-bucket-name`
- `sam deploy` - deploy the packaged SAM template to CloudFormation
  - template file: `sam-template.yml`
  - stack-name: `mystack`
  - capabilities: `CAPABILITY_IAM`
- both `sam package` and `sam deploy` are identical to their AWS CLI equivalents commands `aws cloudformation package` and a`ws cloudformation deploy respectively` - Please consult the AWS CLI command documentation for usage

## CloudFormation & SAM Summary
- SAM is a the Serverless Application Model
- allows you to define and provision serverless applications using CloudFormation
- uses the SAM CLI commands to package and deploy
  - `sam package` - packages yoru application and upload to S3
  - `sam deploy` - deploys your serverless app using CloudFormation