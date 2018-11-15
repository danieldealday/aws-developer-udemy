# Cloud Formation
- a service that allows you to manage, configure, and provision your AWS infrastructure as code
- resources are defined using a CloudFormation template
- CloudFormatoin interprets the template and makes the appropriate API calls to create the resources you have defined
- supports YAML and JSON

## Benefits
- infrastructure is provisioned consistently with fewer mistakes
- less time and effort than configuring things manually
- you can version control and peer review your templates
- free to use (charged for what resource you create)
- can be used to manage updates & dependencies
- can be used to rollback and delete the entire stack as well

## Template
- YAML or JSON template is used to describe the end-state of the infrastructure you are either provisioning or changing
- after creating the template you upload it to CloudFormation using S3
-CloudFormatoin reads the template and makes the API calls on your behalf
- the resulting resources are called a Stack

## Template Structure (YAML)
```yaml
AWSTemplateFormatVersion: "2010-09-09"
Description: "Template to create an EC2 Instace"
Metadata:
  Instances:
    Description: "Web Server Instance"
Parameters: # input values
  EnvType: 
    Description: "Environment Type"
    Type: String
    AllowedValues:
      - prod
      - test
Conditions:
  CreateProdResources: !Equals [!RefEnvType, prod]
Mappings: # e.g. set valus based ona region
  RegionMap:
    eu-west-1:
      "ami": "ami-0bdb1d6c15a40392c"
Transform: # include snippets of code outside the main template
  Name: 'AWS::Include'
  Parameters:
    Location: 's3://MyAmazonS3BucketName/MyFileName.yaml'
Resources: # the AWS resources you are deploying
  EC2Instance:
    Type: AWS::EC2::Instance
    Properties:
      InstanceType: t2.micro
      ImageID: ami-obfb1d6c15a40392c
Outputs:
  InstanceID:
    Description: The Instance ID
    Value: !Ref EC2Instance
```
- resources is the only mandatory section ofthe CloudFormation template
- remember that the Transform section is used to reference additional code stored in S3, allowing for code re-use e.g. for Lambda code or template snippets/re-usable pieces of CloudFormation code

## Summary
- CloudFormation allows you to manage, configure, and provision AWS infrastructre as code (YAML/JSON)
- remmeber that the main sections in the CloudFormation Template:
  - Parameters - input custom value
  - Conditions- e.g. provision resources based on environment
  - Resources - mandatory - the AWS resources to create
  - Mappings - create custom mapping like `Region: AMI`
  - Transforms - reference code located in S3 e.g. Lambda code or re-usable snippets of CloudFormation code

## In-Practice
0. develop your own CloudFormation Template
  - take care that your AMI is specific to the region you are working in
  - makes sure to designate your Parameters, Resources, InstanceSecurityGroup for specific resources, etc.
1. visit CloudFormation in console
2. select a template
  - use design template tool
  - use your own template
  - CloudFormation will save you template to a S3 bucket
3. assign appropriate Key-Pair
4. conigure ability for rollback-failure
  - available from the AWS API
5. create CloudFormation to execute
  - build tasks are available to be viewed
  - instance can be viewed in EC2