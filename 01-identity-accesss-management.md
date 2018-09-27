# Identity Access Management (IAM)
- part of the Security, Identity, & Compliance services of AWS
- allows you to manage users and their level of access to the AWS console

## IAM Services
- centralized control of your AWS account
- shared access to your AWS account
- granular permission
- identity federation (including Dctive Directory, Facebook, LinkedIn, etc.)
- multifactor-authentication (MFA): grants access only after successfully completing multiple authentication mechanisms
- provied temporary access for users/devics and services, as necessary
- allows you to set up your own password rotation policy
- integrates with many different AWS services
- support PCI DSS compliance

## Terminology
- user
- groups - a collection of users under one set of permissions
- roles - you create roles and can then assign them to AWS resources
- policies - a document that defines one or more permissions; can be attached to a user, group or role
- identity provider
- policy documents - JSON objects that reflect sets of permission

## Characteristics
- IAM service is universal and does not apply to regions
- root account is the account created when you first setup your AWS account - it has complete Administrator access
- new users have NO permissions when they are first created
- new users are assigned Access Key ID & Secret Access Keys when they are first created
- these are not the same as a password and you cannot use the Access Key ID & Secret Access Key to login into the AWS Management Console
- Keys are used to access AWS through API and command line
- Keys can only be viewed once, if you lose them, you have to regenerate them (users); they should be saved in a secure location
- alwaays setup Multifactor Authentication (MFA) on your root account
- you can create adn customise your own password rotation policies