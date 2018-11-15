# Summary

## SQS (Simple Ququeing Service)
- SQS is a distributed message queueing system
- SQS allows you to decouple the components of an application so that they are independent
- pull-based not push-based
- standard-queues (default setting): best effort ordering, message delivered at least once
- FIFO queues: ordering strictly perserved, message delivered once, no duplicates (e.g. good for banking transactions which need to happen in strict order)

## SNS (Simple Notification Service)
- SNS is a scalable and highly available notification service which allows you to send push notifications from the cloud
- a variety of message formats are supported: SMS text message, email, Amazon Simple Queue Service (SQS) queues, any HTTP endpoint
- pub-sub model whereby users subscribe to topics
- it is push mechanism rather than a pull mechanism
- example architecture: a company wanting to send notifications to multiple customers could use SNS to fan out multiple messages in SQS format using a dedicated SQS queue per customer

## SNS Versus SES (Simple Email Service)
- remember that SES is for email only
- it can be used for incoming and outgoing mail
- it is not subscription based - yopu only need to know the email address
- SNS caters to various formats: SMS, SQS, HTTP, email
- push notifications only
- pub-sub model - consumers must subscribe to a topic
- you can fan out messages to large number of recipients (e.g. multiple clients each with their own SQS queue)

## Kinesis
- know the difference between the 3 cores services
  - Kinesis Stream  
    - video streams - securely stream video from connected devices to AWS for analytics and machine learning
    - data streams - build custom applications and process data in real-time
  - Kinesis Firehose - capture, transform, load data streams into AWS data stores for near real-time analytics with business intelligence tools
  - you can configure Lambda to subscribe to a Kinesis Stream and execute a function on your behalf when a new record is detected, before sending the processed data on to its final destination

## Elastic Beanstalk
- deploys and scales your web applications including the web application srever platform where required
- supports widely used programming technologies - Java, PHP, Python, Ruby, Go, Docker, .NET, and Node.js
- includes other application server platforms like Tomcat, Passenger, Puma, and IIS (Microsoft Internet Information Services)
- provisions the underlying resources for you
- can fully manage the EC2 instance for you or you can take full administrative control
- updates, monitors, metric creation, and health checking are all included
- 4 Deployment Approaches
  - All-At-Once
    - service interruption while you update the entire environment at once
    - to roll back, you eed to perform a further All-At-Once upgrade
  - Rolling
    - reduced capacity during deployment
    - to roll back, perform a rolling update
  - Rolling with Additional Batch
    - maintains full capacity
    - to roll back, perform a rolling update
  - Immutable
    - preferred option for mission critical production systems
    - maintains full capacity
    - to roll back, just delete the new instance and auto-scaling group
- you can customize your Elastic Beanstalk environment by adding configuration files
- the files are written in YAML or JSON
- files have a `.config` extension
- the `.config` files are saved to the `/.ebextensions` directory
- your `/.ebextensions` directory must be located in the top level directory of your application source code bundle

## RDS & Elastic Beanstalk
- 2 different options for launching your RDS instance
  - With Elastic Beanstalk
    - when you terminate the Elastic Beanstalk environment, the database will also be terminated
    - quick and easy to add your data base and get started
    - suitable to `dev` nad `test` environments only
  - Without Elastic Beanstalk
    - additional configurations steps required - Security Group nd Connection information
    - suitable for Production environments, more flexibility
    - allows connection from multiple environments, you can tear down the application stack without impacting the database