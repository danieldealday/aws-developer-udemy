# API Gateway
- a fully managed service that makes it easy for developer to publish, maintain, monitor and secure APIs at scale
- with a few clicks in the AWS Management console, you can create an API that acts as a "front door" for applicaitons to access data, business logic or functionality from your back-end services, such as applications running on Amazon EC2, code running on AWS Lambda or any web application

## Types of APIs
- REST APIs (representational state transfer)
  - uses JSON
- SOAP APIs (simple object access protocol)
  - uses XML

## Usage
- expose HTTPS endpoints to define a RESTful API
- serverless-ly connect to services like Lambda and DynamoDB
- send each API endpoint to a different target
- run efficiently with low cost
- scale effortlessly
- track and control usage by API key
- throttle requests to prevent attacks
- connect to CloudWatch to log all request for monitoring
- maintain multiple version of your API

## Configuration
- define an API (container)
- define Resources and nested Resrouces (URL paths)
- for each Resource:
  - select supported HTTP methods (verbs)
  - set security
  - choose target (such as EC2, Lambda, DynamoDB, etc.)
  - set requests and response transformations
- deploy API to a Stage
  - uses API Gateway domain, by default
  - can use a custom domain
  - now supports AWS Certification Manager: free SSL/TLS certifications

## API Caching
- cache your endpoint's response
- wich caching, you can reduce the number of calls made to your endpoint and also improve the latency of the request to your API
- when you enable cahcing for a stage, API Gateway caches responses from your endpoint for a specified time-to-live (TTL) period, in seconds, then it response to the request by looking up the endpoint response from the cahce instead of making a request to your endpoint

## Same Origin Policy
- an important concept in the web application security model; a web browser permits scripts contained in a first web page to access data in a second web page, but only if both web pages have the same origin
- this is done to prevent Cross-Site Scripting (XSS) attacks
- enforced by web browsers
- ignored by tools like PostMan software and `curl` command

## Cross-Origin Resource Sharing (CORS)
- one way the server at the other end (not the client code in the browser) can relax the same-origin policy
- CORS is a mechanism that allows restricted resource (e.g. fonts) on a web page to be requested from another domain outside the domain from which the first resource was served
- CORS flow
  - browser makes an HTTP OPTIONS call for a URL
    - OPTIONS is an HTTP method like GET, PUT and POST
  - server return response that says:
    - "These other domains are approved to GET this URL."
  - Error - "Origin policy cnnot be read at the remote resource?"
    - you need to enable CORS on API Gateway

## Tips
- remember what API Gateway is at a high level
- API Gateway has caching capabilities to increase performance
- API Gateway has low cost and scales automatically
- you can throttle API Gateway to prevent attacks
- you can log resutls to CloudWatch
- if yo uare using JavaScript/AJAX that uses multiple domains with API Gateway, ensure that you have enabled CORS on API Gateway
- CORS is enforced by the client