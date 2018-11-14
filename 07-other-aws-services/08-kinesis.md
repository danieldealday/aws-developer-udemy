# Kinesis
- streaming data is data that is generated continuously by thousands of data sources, which typically send in the dat arecords simultaneously and in small sized (order of Kilobytes)
  - purchases from online stores (think amazon.com)
  - stock prices
  - game data (as the gamer plays)
  - social network data
  - geospatial data (think uber.com)
  - iOT sensor data

## What is Kinesis?
- a platform on AWS to send your streaming data
- makes it easy to load and analyze streaming data and also providing the ability for you to build your own custom applications for your business needs

## Kinesis Services
- Kinesis Streams - manual developer management of streams and shards from data producers before piping into other data consumers (EC2 is hit usually first, Redshift, S3, ElasticSearch Cluster, etc.)
- Kinesis Firehose - retains data by default for 24 hours (ability to extend to 7 days); requires no management of streams and shards; data can immediately be analyzed by Lambda; the automated way of managing Kinesis
- Kinesis Analytics - an analysis layer of using SQL queries from Kinesis that can be then sent analyzed data to S3, Redshift, and ElasticSearch Clusters

## Kinesis Streams
- data can come from EC2 instances, mobile phones, computers, and iOT
- data is stored in Shards through Kinesis Streams and then sent to EC2 Consumers and can then send them to DynamoDB/S3/EMR/Redshift
- streams consists of shards
  - 5 transactions per second for READs, up to a maximum total data read rate of 2MB/second and up to 1k records/second for WRITEs, up to a maximum total data write of 1MB/second (including partition keys)
  - the data capacity of your stream is a function of the number of shards that you specify for the stream; the total capacity of the stream is the sum of the capacities of its shards

## Summary
- know the difference between Kinesis Streams and Kinesis Firehose; you will be given scenario questions and you must choose the most relevant service
- understand what Kinesis Analytics is