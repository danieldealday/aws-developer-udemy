# Advanced API Gateway

## Import APIs
- API Gateway Import can be used to import an API from an external definition file into API Gateway
  - currently, the Import API feature supports `Swagger v2.0` definition files
  - with the Import API, you can either create a new API by submitting a POST request that includes a Swagger definition in the payload and endpoint configuration or you can update an existing API by using a PUT request that contains a Swagger definition in the payload; you can update an API by overwriting it with a new definition or merge a definition with an existnig API - you can specify the option using a mode query parameter in the request URL

## API Throttling
- by default, API Gateway limits the steady-state request rate to 10,000 requests per second (rps)
- the maximum concurrent requests is 500 requests across all APIs within an AWS account
- if you go over 10,000 requests per second or 5000 requests you will receive a `429 Too Many Request` error response
- if a caller submits 10,000 requests in a one second period evenly (for example, 10 requests every millisecond), API Gateway processes all requests without dropping any
- if the caller send 10,000 requests in the first millisecond, API Gateway serves 5,000 of those requests and throttles the rest in the one-second period
- if the caller submits 5,000 requests in the first millisecond and then evenly spreads another 5,000 requests through the remaining 999 milliseconds (for example, about 5 requests per millisecond); API Gateway processes all 10,000 requests in the one-second period without returning 429 Too Many Requests error responses
 

 ## SOAP Web Service Passthrough
 - you can configure API gateway as a SOAP web service passthrough

 ## Tips
 - import API's using Swagger 2.0 definition files
 - API Gateway can be throttled
  - default limits are 10,000 RPS or 5,000 concurrently
  - you can configure API Gateway as a SOAP Web Service passthrough