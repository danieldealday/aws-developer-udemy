# Lambda
- a compute service where you can upload your code and create a Lambda function; AWS Lambda takes care of provisioning and managing the servers that you use to run the code - you don't have to worry about operating systems, patching, scaling, etc.

## Usage
- an even-driven compute service where AWS Lambda runs your code in response to events; these events could be changes to data in an Amazon S3 bucket or an Amazon DynamoDB table
- a compute servive to run your code in respont to HTTP requests using Amazon API Gateway or API calls made using AWS SDKs

## Compatible Programming Languages
- Node.js
- Java
- Python
- C#
- Go

## Pricing
- number of requests
  - first 1 million requests are free
  - $0.20 / million requests after
- duration
  - calculate from the time your code begins executing until it returns or otherwise terminates, rounded up to the nearest 100ms
  - the price depends on the amopunt of memory you allocate to your function
  - charged for every $0.000001667 for ever GB/second used

## Benefits
- no servers
- continuous (automated) scaling
- very low cost

## Tips
- Lambda scales out (not up) automatically
- Lambda functions are independent; 1 event = 1 function
- Lambda is serverless
- know what services are serverless
- Lambda functions can trigger other lambda functions; 1 event can = # of functions if functions trigger other functions
- architectures can get extremely complicated; AWS X-ray allows you to debug what is happening
- Lambda can do things globally, you can use it to back up S3 buckets to other S3 buckets etc.
- know your triggers