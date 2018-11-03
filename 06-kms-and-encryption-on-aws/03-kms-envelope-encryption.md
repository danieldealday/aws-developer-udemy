# KMS Envelope Encryption

## Envelope Encryption
- AWS Master Key encrypts the Envelope Key (Data Key)
- Envelope Key (Data Key) Encrypts Data

## Decryption with AWS
- Encrypted Data Key and AWS KMS Master Key is used by the Encryption Algorithm
- Encryption Algorithm creates a Plain Text Data Key
- Plain Text Data Key creates Decrypted Data

## Tips
- Customer Master Key
  - used to decrypt the data key (envelope)
  - Envelope key is used to decrypt the data