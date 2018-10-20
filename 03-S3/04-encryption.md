# S3 Encryption

## Available Types of Encryption
- In-Transit
  - SSL/TSL (Secure Sockets Layer/Transport Layer Security)
- At-Rest
  - Server-Side Encryptions
    - S3 Managed Keys - SSE-S3
    - AWS Key Management Service, Managed Keys, S3-KMS
    - Server Side Encryption with Customer Provided Keys - SSE-C
- Client-Side Encryption

## Enforcing Encryption on S3 Buckets
- every time a file is uploaded to S3, a PUT request is initiated
- this is what a PUT request looks like ...
  ```
  PUT /myFile HTTP/1.1
  Host: myBucket.s3.amazonaws.com
  Date: Wed, 25 Apr 2018 09:50:00 GMT
  Authorization: authorization string
  Content-Type: text/plain
  Content-Length: 27364
  x-amz-meta-author: Faye
  [27364 bytes of object data]
  ```
- if the file is to be encrypted at upload time, the `x-amz-server-side-encryption parameter` will be included in the request header
  - 2 available options
    - `x-amz-server-side-encryption: AES256` (SSE-S3 - S3 managed keys)
    - `x-amz-server-side-encryption: ams:kms` (SSE-KMS - KMS managed keys)
  - when this parameter is included in the header of the PUT request, it tells S3 to encrypt the oject at the time of upload, using the specified encryption method
  - you can enforce the use of Server-Side Encryption by using a Bucket Policy which denies any S3 PUT request which doesn't include the `x-amz-server-side-encryption parameter` in the request header

## Summary
- Encryption In-Transit
  - SSL/TLS (HTTPS)
- Encryption-At-Rest
  - Server-Side
    - SSE-S3
    - SSE-KMS
    - SSE-C
  - Client-Side
- If you want to enforce the use of encryption for your files stored in S3, use an S3 Bucket Policy to deny all PUT requests that don't included the `x-amz-server-side-encryption` parameter in the request header