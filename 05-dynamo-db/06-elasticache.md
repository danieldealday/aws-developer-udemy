# Elasticache
- in-memory cache in the cloud
- improves performance of web applications, allowing you to retrieve information from fast in-memory caches rather than slower disk-based databases
- sits between your application and the database e.g. an application frequently requesting specific product information for your best selling products
- takes the load off your databases
- good if your database is particularly read-heavy and the data is not changing frequently

## Benefits and Use Cases
- improves performance for read-heavy workloads e.g. social networking, game media sharing, Q&A portals
- frequently accessed data is stored in memory for low-latency access, improving the overall performance of your application
- also good for compute heavy workloads e.g. recommendation engines
- can be used to store results of input-output intensive database queries or output of compute-intensive calculations

## Types of Elasticache
- Memcached
  - widely adopted memory object caching system
  - multi-threaded
  - no multi-AZ capability
- Redis
  - open-source in-memory key-value store
  - supports more complex data structures: sorted sets and lists
  - supports Master/Slave replication and Multi-AZ for cross AZ redundancy

## Caching Strategies
- 2 strategies available: Lazy Loading and Write-Through
- Lazy Loading - loads the data in to the cache only when necessary
  - if requested data is in the cache, Elasticache returns the data to application
  - if the data is not in the cache or has expired, Elasticache returns `null`
  - you application then fetches the data from the databse and writes the data received into the cache so that it is available next time
  - Advantages
    - only requested data cached: avoids filling up cache with useless data
    - node failures are not fatal a new empty node will just have a lot of cache misses intially
  - Disadvantages
    - cache miss penalty: intitial request, query to database, writing of data to the cache
    - stale data: if data is only updated when there is a cache miss, it can become stale; doesn't automatically update if the data in the database changes
- Time-To-Live (TTL)
  - specifies the number of seconds until the key (data) expires to avoid keeping stale and data in the cache
  - lazy loading treats an expired key as a cache miss and causes the application to retrieve the data from the database and subsquently write the data into the cache with a new TTL
  - does not eliminate stale data - but helps to avoid it
- Write Through - adds or updates data to the cache whenever data is written to the database
  - Advantages
    - data in the cache, never state
    - users are generally more tolerant of additional latency when updating data than when retrieving it
  - Disadvantages
    - write penalty: every write involves a write to the cache as well as a write to the database
    - if a node fails and a new one is spun up, data is missing until added or updated in the database (mitigate by implementing lazy loading in conjunction with write-through)
    - wanted resources if most of the data is never read

## Tips
- in-memory cache sits between your application and database
- 2 different caching strategies: lazy loading and write through
- lazy loading only caches the data when it is requested
- elasticache node failures not fatal, just lots of cache misses
- cache miss pentalty: initial request, query database, writing to cache
- avoid stale data by implementing TTL
- write through strategy writes data into the cache whenever there is a change to the database
- data is never stale
- write penalty: each write involves a write to the cache
- elasticahce node failure means that data is missing until added or updated in the database
- wasted resources if the most of the data is never used