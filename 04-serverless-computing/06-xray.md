# X-Ray
- a service that collects data about requests that your application serves and provides tools you can use to view, filter and gain insights into that data to identify issues and opportunities for optimizations
- for any traced request to your application, you can see detailed information not only about the request and response, but also about calls that your application makes to downstream AWS resources, microservices, databases and HTTP web APIs

## X-Ray SDK
- Provides:
  - Interceptors to add to your code to trace incoming HTTP requests
  - Client Handlers to instrument AWS SDK clients that your application uses to call other AWS services
  - an HTTP client to use instrument calls to other internal and external HTTP web services

## Compatible AWS Integrations
- Elastic Load Balancing
- Lambda
- API Gateway
- EC2
- Elastic Beanstalk

## Supported Languages
- Java
- Go
- Node.js
- Python
- Ruby
- .Net