# S3 Summary
- S3 is object-based e.g. allows you to upload files
- files can be from 0Bytes to 5TB
- unlimited storage
- files are stored in Buckets (think folder/directory)
- S# is a universal namespace; names must be unique globally
  - `https://s3-eu-west-1.amazonaws.com/examplebucket`
- Read after Write consistency for PUTS of new objects
- Eventual consistency for overwrite PUTS and DELETES (can take some time to propagate)

## S3 Storage Classes/Tiers
- S3 (durability, immediately available, frquently accessed)
- S3 - IA (durable, immediately available, infrquently accessed)
- S3 - One Zone IA: same as IA, however, dat ais stored in a single Availability Zone only
- S3 - Reduced Redundancy Storage (data that is easily reproducible, such as thumbnails, etc.)
- Glavier - archived data, where you can wait 3 to 5 hours before accessing

## Core Fundamentals of an S3 Object
- key (name)
- value (data)
- version
- metadata (data about data)
- subresources (used to manage bucket-specific configuration)
    - bucket policies, ACLs
    - CORS
    - transfer acceleration
- object-based storage only (files-only)
- not suitable to install an operating system on
- successful upload will generate an HTTP 200 status code

## Security
- all newly create buckets are PRIVATE by default
- you can set up access control to you buckets using ...
    - Bucket Policies - applied at a bucket level
    - Access Control Lists - applied at an object level
- S3 buckets can be configured to create access logs, which log all requests made to the S3 bucket; these logs can be written to another bucket

## Encryption
- Types
    - In-Transit
        - SSL/TLS
    - At-Rest
        -   Server Side
            - SSE-S3
            - SSE-KMS
            - SSE-C
        - Client Side
- remember that we can use a bucket policy to prevent unencrypted files ffrom being uploaded by using creating a policy which only allows requets which include the `x-amz-server-side-encryption` parameter in the request header

## Cross Origin Resource Sharing (Cors)
- used to enable cross origin access for your AWS resources
- e.g. S3 hosted website accessing JavaScript or image files located in another S3 bucket
- by default resources in one bucket cannot access resources located in another
- to allow this we need to configure CORS on the bucket being accessed and enable access for the origin (bucket) attempting to access
- always use the S3 website URL, not the regular bucket URL:
    ```
    * this one
    http://daniels3.s3-website.eu-west-1.amazonaw.com
    ** NOT this one
    https://s3-eu-west-1.amazonaws.com/daniels3
    ```

## CloudFront
- Edge Location - the location where content will be cached; this is seperate to an AWS region/AZ
- Origin - the origin of all the files that the CDN will distribute; origins can be an S3 bucket, an EC2 instance, an Elastic Load Balancer or Route53
- Distribution - the name given the CDN, which consists of a collection of Edge Locations
    - Web Distribution - typically used for websites
    - RTMP - used for media streaming
- edge locations are not just READ-only - you can WRITE to them too i.e. put an object on to them
- objects are cached for the life of the TTL (time to live)
- you can clear cached objects, but you will be charged (invalidation)

## Performance Optimization
- 2 Maain Approaches for S3
    - GET-intensive Workloads - used CloudFront
    - (UPDATE!!! NO LONG REQUIRED as of JULY 2018) Mixed Workloads - avoid sequential key names for your S3 objects, instead, add a random prefix like a hex hash to the key name to prevent multiple objects from being stored on the same partition

## [Read the FAQ](https://aws.amazon.com/s3/faqs)