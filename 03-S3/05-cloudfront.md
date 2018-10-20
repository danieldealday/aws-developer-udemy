# S3 CloudFront
- used to deliver your entire website, including dynamic, static, streaming and interactive content using a global network of edge locations; requests for your content are automatically routed to the nearest edge location, so conenti is delivered with the best possible performance
- can be used to optimize performance for users accessing a website backed by S3
- optimized to work with other Amazon Web Services: S3, EC2, Elastic Load Balancing and Route 53
- CloudFront also works seamlessly with any non-AWS origin server, which stores the original, definitive versions of your files

## Content Delivery Network (CDN)
- a system of distributed servers (network) that deliver webpages and other web content to a user based on the geographic locations of the user, the origin of the webpage and a content delivery server

## Terminology
- Edge Location - the location where content is cached and can also be written; seperate to an AWS Region/AZ
- Origin - the origin of all the files that the CDN will distribute; Origins can be an S3 Bucket, an EC3 Instance, an Elastic Load Balancer, or Route 53
- Distribution - the name given the CDN, which consists of a collection of Edge Locations
- Web Distribution - typically used for websites
- RTMP - used for media streaming

## Distribution Types
- Web - used for websites, HTTP/HTTPS
- RTMP - (Adobe Real Time Messaging Protocol) used for media streaming / Flash multimedia content

## CloudFront and S3 Transfer Acceleration
- enables fast, easy and secure transfers of files over long distance between your end users and an S3 Bucket
- takes advantage of Amazon CloudFront's global distribution edge locatoin; as the data arrives at an edge location, data is routed to Amazon S3 over an optimized network path

## Summary
- Edge Location - the location where content will be cached; this is seperate to an AWS Region/AZ
- Origin - the origin of all the files that the CDN will distribute; origins can be an S3 Bucket, an EC2 instance, an Elastic Load Balancer or Route 53
- Distribution - the name given the CDN, which consists of a collection of Edge Locations
  - Web Distribution - typically used for websites
  - RTMP - used for media streaming
- Edge Locations are not just READ-ONLY -- you can WRITE to them too (PUT an object on to them)
- CloudFront Edge Locations are utilised by S3 Transfer Acceleration to reduce latency for S3 uploads
- objects are cached for the TTL (time-to-live)
- you can clear cached objects, but you will be charged