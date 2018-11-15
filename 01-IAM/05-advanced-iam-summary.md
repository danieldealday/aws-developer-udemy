# Advanced IAM Summary

## Web Identity Federation
- Federation allows users to authenticate with a Web Identity Provider (Google, Facebook, Amazon)
- the user authenticates first with the WebID Provider and receives an authentication token, which is exchanged for temporary AWS credentials allowing them to assume an IAM role

## Cognito
- Cognito is an Identity Broker which handles interaction between your applications and the Web ID provider (you don't need to write your own code to do this)
  - provides sign-up, sign-in and guest user access
  - syncs user data for a seamless experience across your devices
  - Cognito is the AWS-recommended approach for Web ID Federation
- Cognito uses User Pools to manage user sign-up and sign-in directly or via Web Identity Providers
- Cognito uses Push Synchronization to send a silent push notification of user data updates to multiple device types associated with a user ID

## Type of IAM Policies
- Managed Policy - AWS-managed default policies
- Customer Managed Policy - managed by you
- Inline Policy - managed by you and embedded ina single user, group, or role
- in most cases, AWS recommends using managed policies over inline policies