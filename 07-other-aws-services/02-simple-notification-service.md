# Simple Notification Service (SNS)
- a web service that makes it easy to set up, operate and send notifications from the cloud
- it provides developers with a highly scalable, flexible and cost-effective capability to publish messages from an application and immediately deliver them to subscribers or other applications
- e.g. push notifications to Apple, Google, Fire OS and Windows devices, as well as Android devices in China with Baidu Cloud Push
- besides pusing cloud notifications directly to mobile devices, Amazon SNS can also deliver notifications by SMS text message or email to Amazon Simple Queue Service (SQS) queues or to any HTTP endpoint
- SNS notifications can also trigger Lambda functions: when a message is published to an SNS topic that has a Lambda function subscribed to it, the Lambda function is invoked with the payload of the published message; the Lambda function receives the message payload as an input parameter and can manipulate the information in the message, publish the message to another SNS topic or send the message to other AWS services

## Topics
- allows you to group multiple recipients using topics; a topic is an "access point" for allowing recipients to dynamically subscribe for identical copies of the same notification
- one topic can support deliveries to multiple endpoint types - for example, you can group together iOS, Android and SMS recipients; when you publish once to a topic, SNS delivers appropirately formatted copies of your message to each subscriber
- to prevent messages from being lost, all messages published to Amazon SNS are stored redundantly across multiple availability zones

## Benefits
- instantaneous, push-based delivery (no pullin)
- simple APIs and easy integration with applications
- flexible message delivery over multiple transport protocols
- inexpensive, pay-as-you-go model with no up-front costs
- web based AWS Management Console offers the simplicity of a point-and-click interface

## SNS versus SQS
- both are messaging services in AWS
- SNS is a push-based messaging system

## Pricing
- $0.50 / 1 million Amazon SNS requests
- $0.06 / 100k notification deliveries over HTTP
- $0.75 / 100 notification deliveries over SMS
- $2.00 / 100k notification deliveries over email

## Characteristics
- SNS follows the "publish-subscribe" (pub-sub) messaging paradigm with notifications being delivered to clientsusing a "push" mechanism that elimanates the need to periodically check of "poll" for new information and updates
- with simple APIs requiring minimal up-front development effort, no maintenance or management overhead and pay-as-you-go-pricing, Amazon SNS gives developers an easy mechanism to incorporate a powerful notification system with their applications

## Tips
- SNS is a scalable and highly available notification service which allos you to send push notifications from the cloud
- variety of message formats supported: SMS text message, email, Amazon Simple Queue Service (SQS) queues, any HTTP endpoint
- pub-sub model whereby users subscribe to topics
- it is a push mechanism, rather than a pull (poll) mechanism