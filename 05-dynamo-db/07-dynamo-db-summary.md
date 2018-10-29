# DynamoDB Summary
- Amazon DynamoDB is a low-latency NoSQL database
- consists of Tables, Item and Attributes
- supports both document and key-vaue data models
- supported document formats are JSON, HTML, XML
- 2 types of Primary Keys: Partition Key and combination of Parition Key + Sort Key (Composite Key)
- 2 Consistency models: Strongly Consistent / Eventually Consistent
- access is controlled using IAM policies
- fine-grained access control using IAM Condition parameters: `dynamodb:LeadingKeys` to allow users to access only the items where the partition key value matches their user ID

## Indexes
- indexes enable fast queries on specific data columns
- give you a different view of your data based on alternative partition / sort keys
- important to understand the differences
  - Local Secondary Index
    - must be created at when you create your table
    - same parition key as your table
    - different sort key
  - global secondary index
    - can create any time - at a table creation or after
    - different partition key
    - different sort key

## Scan versus Exam
- a query operation finds items in a table using only the Primary Key attribute
- you provide the Primary Key name and a distinct value to search for
- a scan operation examines every item in the table
  - by default, returns all data attributes
- use the `ProjectionExpression` parameter to refine the results
- query results are always sorted by the Sort Key (if there is one)
- sorted in ascending order
- set `ScanIndexForward` parameter to `false` to reverse the order - queries only
- query operation is generally more efficient than a scan
- reduce the impact of a query or scan by setting a samller page size which uses fewer read operations
- isolate scan operations to specific tables and segregate them from your mission-critical traffic
- try parallel scans rather than the default sequential scan
- avoid using scan operations if you can: design tables in a way that you can use the Query, Get or BatchGetItem APIs

## Provisioned Throughput
- provisioned throughput is measured in capacity units
- 1 x Write Capacity Unit = 1 x 1KB Write per second
- 1 x Read Capacity Unit = 1 x 4KB Strongly Consistent Read OR 2 x 4KB Eventually Consistent Reads per second
- Calculate Write Capacity Requirements (100 x 512 byte items per second):
  - first, calculate how many Capacity Units for each write: Size of each item / 1KB (for Write Capacity Units)
  - rounded-up to the nearest whole number, each write will need 1 x Write Capacity Unit per write operation
  - multiplied by the number of writes per second = 1 x 100 = 100 Write
- Capacity Units Requirements (80 x 3KB items per second):
  - first, calculate how many Capacity Units for each read: Size of each itemm / 4KB (for Read Capacity Units)
  - rounded-up to the nearest whole number, each read will need 1 x Read Capacity Unit operation
  - multiplied by the number of reads per second = 1 x 80 = 80 Read Capacity Units required or Strongly Consistent, but if Eventual Consistency is acceptable divide by 2 = 40 Read Capacity Units required

## DAX
- provides in-memory caching for DynamoDB tables
- improves response times for Eventually Consistent reads only
- you point your API calls to the DAX cluster instead of your table
- if the item you are querying is on the cache, DAX will return it; otherwise, it will perform an Eventually Consistent GetItem operation to your DynamoDB table
- not suitable for write-intensive applications or applications that require Strongly Consistent reads

## Elasticache
- in-memory cache sits between your application and database
- 2 different caching strategies: lazy loading and write through
- lazy loading only caches the data when it is requested
- elasticache node failures not fatal, just lots of cache misses
- cache miss penalty: initial request, query database, writing to cache
- avoid stale data by implementing a TTL
- jwrite through strategy writes dat into the cache whenever there is a change to the database
- data is never stale
- write penalty: each write involves a write to the cache
- elasticache node failure means that data is missing until added or update in the database
- wasted resources if most of the data is never used