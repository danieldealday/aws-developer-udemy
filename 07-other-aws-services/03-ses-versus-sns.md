# SES versus SNS

## Amazon SES (Simple Email Service)
- a scalable and highly available email service desinged to help marketing teams and application develoepr send marketing, notification, and transactional emails to their customers using a pay as you model
- can also be used to receive emails: incoming mails can be delivered automatically to an S3 bucket
- incoming mails can be used to trigger Lambda functions and SNS notifications

### SES Use Cases
- automated emails
- purchase confirmations, shipping notifications, order status updates
  - e.g. a mobile phone company that needs to send automated confirmation email every time a customer purchases pre-paid mobile phone minutes
- marketing communication, advertisements, newsletters, special offers
  - e.g. an online retail business that needs to let customers know about sales promotions and discount

## SES vs SNS Comparison
- SES
  - email messaging service
  - can trigger Lambda function or SNS notification
  - can be used for both incoming and outgoing email
  - an email address is all that is requred to start sending messages to a user
- SNS
  - pulisher-subscriber messaging service, formats include SMS, HTTP, SQS, email
  - can be used to trigger Lambda function
  - can fan out messages to large number of recipients (replicate and push messages to multiple endpoints and formats)
  - consumers must subscribe to a topic to recieve the notifications

## Tips
- remember that SES is for email only
- it can be used for incoming and outgoing mail
- it is not subscription-based, you only need to know the email address
- SNS supports multiple formats (SMS, SQS, HTTP, email)
- push notifications only
- pub/sub model: consumer must subscribe to a topic
- you can fan-out messages to large number of recipients
  - e.g. multiple clients each with their own SQS queue