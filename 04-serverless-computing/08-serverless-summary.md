# Serverless Summary
- Lambda scales out (not up) automatically
- Lambda functions are independent; 1 event = 1 function
- Lambda is serverless
- know what services are serverless
- Lambda functions can trigger other lambda functions; 1 event can = # of functions if functions trigger other functions
- architectures can get extremely complicated, AWS X-Ray allows you to debug what is happening
- Lambda can do things globally, you can use it to back up S3 buckets to other S3 buckets etc.
- know your trigger


## API Gateway
- remember what API Gateway is at a high level
- API Gateway has cahing capabilties to increase performance
- API Gateway is low cost and scales automatically
- you can throttle API Gateway to prevent attacks
- you can log results to CloudWatch
- if you are using JavaScript/AJAX that uses multiple domains with API Gateway, ensure that you have enabled CORS on API Gateway
- CORS enforced by the client

## Version Control
- can have multiple versions of lambda functions
- latest version will use `$LATEST`
- qualified version will use `$LATEST`, unqualified will not have it
- versions are immutable
- can split traffic using aliases to different versions
  - can not split traffice with `$LATEST`, instead create an alias to lateset

## Step Functions
- great way to visualize your serverless applicatoin
- step functions automatically triggers and tracks each step
- step functions logs the state of each step so if something goes wrong you can track what went wrong and where

## X-Ray
- X-ray software developer kit (SDK)
  - interceptors to add to your code to trace incoming HTTP requests
  - client handlers to instrument AWS SDK clients that your application uses to call other AWS services
  - an HTTP client to use to instrument calls to other internal and external HTTP web services
- integration with AWS
  - Elastic Laod ZBalancing
  - Lambda
  - API Gateway
  - Elastic Compute Cloud (EC2)
  - Elastic BeanStalk
- compatible programming languages
  - Java
  - Go
  - Node.js
  - Python
  - Ruby
  - .Net