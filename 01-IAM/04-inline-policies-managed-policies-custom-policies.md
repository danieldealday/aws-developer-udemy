# Inline vs. Managed vs. Custom Policies

## Advanced IAM Policies
- IAM is used to define user access permission within AWS
- 3 Types of Policies Available
  - managed
  - customer managed
  - inline

## Managed Policies
- a managed policy is an IAM policy which is created and administered by AWS
- AWS provides managed policies for common use cases based on job function e.g. AmazonDynamoDBFullAccess, AWSCodeCommitPowerUser, AmazonEC2ReadOnlyAccess etc.
- these AWS-provided policies allow you to desing appropriate permissions to your users, groups and roles without having to write the policy yourself
- a single managed policy can be attached to multiple users, groups, or roles within the same AWS account and across different accounts
- you cannot chagne the permissions defined in an AWS managed policy

## Customer Managed Policies
- a customer managed policy is a standalone policy that you create and administer inside yoru own AWS account; you can attach this policy to multiple users, groups, and roles - but only within your own account
- in order to create a customer managed policy, you can copy an existing AWS managed policy and customize it to fit the requirements of your organization
- recommended for use cases where the existing AWS managed policies don't meet the needs of your environment

## Inline Policies
- an inline policy is an IAM policy which is actually embedded within the usre, group, or role to which it applies; there is a strict 1-to-1 relationship between the entity and the policy
- when you delete the user, group, or role in which the inline policy is embedded, the policy will also be deleted
- in most cases, AWS recommends using managed policies over inline policies
- inline policies are useful when you want to be sure that the permissions in a policy are not inadvertantly assigned to any other user, group or role than the one for which they're intended e.g. you are creating a policy that must only ever be attached to a single user, group or role