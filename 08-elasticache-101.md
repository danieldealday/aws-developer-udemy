# Elasticache 101
- a web service that makes it easy to deploy, operate, and scale an in-memory cache in the cloud
- improves the performance of web applications by allowing you to retrieve information from fast, managed, in-memory caches, instead of relying entirely on slower disk=based databases
- can be used to significantly improve latency and throughput for many read-heavy application workloads (such as social networking, gaming, media sharing and Q&A portals) or compute-intensive workloads (such as recommendation engine)
- caching improves performance by storing critical pieces of data in memory for low-latency access
- cached information may include the results of I/O-intensive database queries or the results of computationally-intensive calculations


## Types of Elasticache
- Memcached 
  - a widely adopted memory object caching system
  - Elasticache is protocol compliant with Memcached, so popular tools that you use today with existing Memcached environments will work seamlessly with the service
  - designed as a pure caching solution with no persistence
  - Elasticache manages Memcached nodes as a pool that can grow and shrink, similar to Amazon EC2 Auto Scaling Group
  - individual nodes are expendable and Elasticache provides additional capabilities here such as automatic node replacement and Auto Discovery
  - Use Cases
    - primary goal for object caching to offload workload from database
    - provides a simple caching model
    - running large cache nodes and require multithreaded performance with utilization of multiple cores
    - scaling cache horizontally
- Redis
  - a popular open-source in-memory key-value store that supports dta structures such as sorted sets and lists
  - Elasticache supports Master/Slave replication and Multi-AZ which can be used to cross AZ redundancy
  - Use Cases
    - for advanced data types: lists, hashes and sets
    - sorting and ranking datasets in memory such as leaderboards
    - data persistence of key store
    - run in multiple AWS Availability Zones (Multi-AZ) with failover

## Tips
- exam will give a scenario where a particular database is under a lot of stress/load and you may be asked which service you should use to alleviate this
- Elasticache is a good choice if your database is particularly read-heavy and not prone to frequent changing
- Redshift is a good answer if the reason your database is feeling stress is because management keeps running OLAP transactions on it etc.
- Use Memcache if
  - object caching is your primary goal
  - you want to keep things as simple as possible
  - you want to scale your cache horizontally (scale out)
- Use Redis if
  - you have advanced data types such as lists, hashes and sets
  - you are doing data sorting and ranking such as leader boards
  - data persistence
  - Multi AZ
  - publisher/subscriber capabilities are needed