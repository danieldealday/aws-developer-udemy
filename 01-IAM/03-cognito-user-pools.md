# Cognito User Pools
- User Pools - directories used to manage sign-up and sign-in functionality for mobile and web applications
  -user can sign-in directly to the User Pool or indirectly via n identity provider like Facebook, Amazon, or Google
    - Cognito acts as an Identity Broker between the ID provider and AWS
    - successful authentication generates a number of JSON Web tokens (JWTs)
- Identity Pools - enable you to create unique identities for your users and authenticate them with identity providers
  - with an identity, you can obtain temporary, limited-privilege AWS credentials to access other AWS services

## Push Synchronization
- Cognito tracks the association between user identity and the various different devices they sign-in from
- in order to provide a seamless user experience for your application, Cognito uses Push Synchronization to push updates and synchronize user data across multiple devices
- Amazon SNS is used to send a silent push notification to all the devices associated with a given user identity whenever data stored in the cloud changes

## Summary
- Cognito uses User Pools to manage user sign-up and sign-in directly or viaWeb Identity Providers
- Cognito acts as an Identity broker, handling all interaction with Web Identity Providers
- Cognito uses Push Synchronization to send a silent push notification of user data updates to multiple device types associated with a user ID