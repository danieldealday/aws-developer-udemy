# S3 Performance Optimization
- S3 is designed to support high requerst rates
- if S3 buckets are routinely receiving > 100 PUT/LIST/DELETE or >300 GET requests per second, then there are some best practice guidelines that will help optimize S3 performance
- Guidance is based on the type of workload you are running
  - GET Intensive Workloads - use CloudFront content delivery service ot get best performance; CloudFront will cache your most frequently accessed objects and will reduce latency for your GET requests
  - Mixed Request Type Workloads - a mix of GET, PUT, DELETE, GET Bucket - the key names you use for your objects can impact performance workloads
- S3 uses the key name to determine which partition an object will be stored in
- the use of  sequential key names e.g. names prefixed with a time stamp or alphabetical sequence increases the likelihood of having multiple objects stored on the same partition
- for heavy workloads this can cause I/O issues and contention
- by using a random prefix to key name, you can force S3 to distribute your keys across multiple partition, distributing the I/O workload


## Key Name Example
- the following sequential Key Names are not optimal:
  ```
  - mybucket/2018-08-22-09-00-00/cust1234234/photo1.jpg
  - mybucket/2018-08-22-09-00-00/cust3857422/photo2.jpg
  - mybucket/2018-08-22-09-00-00/cust1248473/photo3.jpg
  ```
- for optimal performance, introduce some randomness into the key name, e.g. prefix the key name with a 4-character hexadecimal hash
  ```
  - mybucket/7eh4-2018-08-22-09-00-00/cust1234234/photo1.jpg
  - mybucket/h35d-2018-08-22-09-00-00/cust3857422/photo2.jpg
  - mybucket/o3n6-2018-08-22-09-00-00/cust1248473/photo3.jpg
  ```

