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
- Redis
  - a popular open-source in-memory key-value store that supports dta structures such as sorted sets and lists
  - Elasticache supports Master/Slave replication and Multi-AZ which can be used to cross AZ redundancy