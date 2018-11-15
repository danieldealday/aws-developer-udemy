# Web Identity Federation
- allows you to give user access to AWS resources after they have successfully authenticated with a web-based identity provider like Amazon, Facebook, or Google
- following successful authentication, the user receives an authentication code from the WebID provider, which they can trade for temporary AWS security credentials

## Amazon Cognito
- provides Web Identity Federation with the following features:
  - sign-up and sign-in to your apps
  - access for guest users
  - acts as an Identity Broker between your application and WebID providers, so you don't need to write any additional code
  - synchronized user data for multiple devices
  - recommended for all mobile applications AWS services

## Amazon Cognito Use Cases
- Cognito brokers between the app and Facebook/Google/Amazon to provide temporary credentials which map to an IAM role allowing access to the required resources
- no need for the application to embed or store AWS credentials locally on the device and it gives users a seamless experience across all mobile devices

## Summary
- Federation allows users to authenticate with a Web Identity Provider (Google, Facebook, Amazon)
- the user authenticates first with the WebID Provider and receives an authentication token, which is exchanged for temporary AWS credentials allowing them to assume an IAM role
- Cognito is an Identity Broker which handles interaction between your applications and the WebID Provider (you don't need to write your own code to do this)
  - provides sign-up, sign-in, and guest user access
  - syncs user data for a seamless experience across your devices
  - Cognito is the AWS recommended approach for Web ID Federation particularly for mobile apps