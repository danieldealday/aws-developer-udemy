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
- Kinesis Streams
- Kinesis Firehose
- Kinesis Analytics

## Kinesis Streams
- data can come from EC2 instances, mobile phones, computers, and iOT
- data is stored in Shards through Kinesis Streams and then sent to EC2 Consumers and can then send them to DynamoDB/S3/EMR/Redshift

###