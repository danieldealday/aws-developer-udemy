# Dynamo DB Accelerator (DAX)
- a fully managed, clustered in-memory cache for Dynamo DB
- delivers up to a 10x read performance
- microsecond performance for millions of requets per second
- ideal for read-heavy and bursty workloads e.g. auction applications, gaming and retail sites during Black Friday promotions

## How Does It Work?
- DAX is a write-through caching service - this means data is written to the cache as well as the back end store at the same time
- allows you to point your DynamoDB API calls at the DAX cluster
- if the item you are querying is in the cach (cache hit), DAX returns the result to the application
- if the item is not available (cache miss) then DAX performs an Eventually Consistent GetItem operation against DynamoDB
- retrieval of data from DAX reduces the read load on DynamoDB tables
- may be able to reduce Provisioned Read Capacity

## What Is It NOT Suitable For?
 - caters for Eventually Consistent reads only - so not suitable for applications taht require Strongly Consistent reads
 - write intensive applications
 - applications that do not perform many read operations
 - application that do not require micro-second response times

 ## Tips
  - provides in-memory caching for DynamoDB tables
  - improves response times for Eventually Consistent reads only
  - you point your API calls the DAX cluster, instead of your table
  - if the item you are querying is on the cache, DAX will return it; otherwise it will perform and Eventually Consistent GetItem operation to your DynamoDB table
  - not suitable for write-intensive applications or applications that require Strongly Consistent reads