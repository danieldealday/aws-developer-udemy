# SQS
- a web service that gives you access to a message queue that can be used to store messages while waiting for a computer to process them
- Amazon SQS is a distributed queue system that enables web service applications to quickly and reliably queue messages that one component in the application generates to be consumed by another component
- a queue is a temporary repository for messages that are awaiting processing

## What is SQS?
- using Amazon SQS, you can decouple the components of an application so they run independently, easing message management between components
- any component of a distributed application can store messages in the queue
- messages can contain up to 256KB of text in any format
- any component can later retrieve the messages programmatically using the Amazon SQS API
- the queue acts as a buffer between the compnent producing and saving data and the component receiving the data for processing
- this means the queue resolves issues that arise if the producer is producing work faster than the consumer can process it or if the producer or consumer are only intermittently connected to the network

## Queue Types

### Standard Queues
- Amazon SQS offers standard as the default queue type
- ets you have a nearly-unlimited number of transactions per second
- guarantee that a message is delivered at least once, however, occasionally (because of the highly-distributed architecture that allows high throughput), more than one copy of a message might be delivered out of order
- provide the best-effort ordering which ensures that messages are generally delivered in the same order as they are sent

### FIFO Queues
- complements the standard queue
- the most important features of this queue type are FIFO (first-in-first-out) delivery and exactly-once processing: the order in which messages are sent and received is strictly preserved and a message is delivered once and remains available until a consumer processes and deletes it
- duplicated are not introduced into the queue
- FIFO queues also suport message groups that allow multiple ordered message groups within a single queue
- FIFO queues are limited to 300 transactions per second (TPS), but have all the capabilities of standard queues

## Key Facts
- SQS is pull-based
- messages are 256 KB in size
- messages can be kept in the queue from 1 minute to 14 days
- defaul retention period is 4 days
- SQS guarantees that your messages will be processed at least once

## Visibility Timeout
- the amount of time that the message is invisible in the SQS queue after a reader picks up that message; provided the job is processed before the visibility time out expires, the message will then be deleted from the queue - if the job is not processed within that time, the message will become visible again and another reader will process it... this could result in the same message being delivered twice
- default visibility timeout is 30 seconds
- increase it if your task takes greater than 30 seconds
- maximum is 12 hours