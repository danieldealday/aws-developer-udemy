# Relational Database Service (RDS)
- SQL database AWS available types
  - SQL Server
  - Oracle
  - MySql Server
  - PostgreSQL
  - Aurora (Amazon)
  - MariaDB

## Data Warehousing
- used for business intelligence (strategies and technologies used by enterprises for the data analysis of business information)
  - Cognos
  - Jaspersoft
  - SQL Server Reporting Services,
  - Oracle Hyperion
  - SAP NetWeaver
- used to pull in large, complex data sets
- usually used by management to do queries on data such as current performance versus targets

## OTLP versus OLAP
- Online Transaction Processing (OLTP) differfrom from Online Analytics Processing (OLAP) in terms of the types of queries you will run
  - OLTP example: Order #2120121 pulls up a row of data such as Name, Date, Address to Deliver to, Delivery Status etc.
  - OLAP example: Net Profit for EMEA and Pacific for the Digital Radio Product, pulls in large numbers of records; sum of radio solid in EMEA, sum of radios sold in Pacific, unit cost of radio in each regions, sales prices of each radio, sales price/unit cost ratio
- data warehousing databases use different type of architecture both from a database perspective and infrastructure layer

## ElasitCache
- a web service that makes it easy to deploy, operate, and scale an in-memory cache in the cloud
- improve the performance of web applications by allowing you to retrieve information form fast, managed, in-memory caches, instead of relying entirely on slower disk-based databases
- supported open-source in-memory caching engines
  - Memcached
  - Redis

## Summary
- RDS - OLTP
  - SQL
  - MySQL
  - PostgreSQL
  - Oracle
  - Aurora
  - MariaDB
- DynamoDB - NoSQL
- RedShift - OLAP (business intelligence & big data)
- ElastiCache - in-memory caching:
  - Memcached
  - Redis