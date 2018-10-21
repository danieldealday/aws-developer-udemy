# S3 Summary
- S3 is object-based e.g. allows you to upload files
- files can be from 0Bytes to 5TB
- unlimited storage
- files are stored in Buckets (think folder/directory)
- S# is a universal namespace; names must be unique globally
  - `https://s3-eu-west-1.amazonaws.com/examplebucket`
- Read after Write consistency for PUTS of new objects
- Eventual consistency for overwrite PUTS and DELETES (can take some time to propagate)
- 