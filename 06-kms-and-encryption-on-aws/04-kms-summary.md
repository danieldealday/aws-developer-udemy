# KMS Summary
- a managed service that makes it easy for you to create and control the encryption keys used to encrypt your data
0 AWS KMS is integrated with other AWS services including EBS, S3, Amazon Redshift, Amazon Elastic Transcoder, Amazon WorkMail, Amazon Relational Database Service (Amazon RDS), and others to make it simple to encrypt your data with encryption keys that you manage

## Customer Master Key (CMK)
- alias
- creation date
- description
- key state
- key material (either customer provided or AWS provided)
- can never be exported

### Setup
- create Alias and Description
- choose material option
  - define key Administrative Permission
    - IAM users/roles that can administer (but not use) the key through the KMS API
  - define key Usage Permissions
    - IAM users/roles that can use the key to encrypt and decrypt data
  - key material options
    - use KMS generated key material
    - your own key material

## KMS API Calls
- aws kms encrypt
- aws kms decrypt
- aws kms re-encrypt
- aws kms enable-key-rotation

## Envelope Encryption
- Customer Master Key
  - CMK used to decrypt the data key (envelope key)
  - envelope key is used to decrypt the data