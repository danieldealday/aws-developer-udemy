# Simple Storage Service (S3) - 101
- provides developers and IT teams with secure, durable, highly-scalable object-based storage
- Used for ...
  - files, images, web pages
  - not operating systems or databases
- easy to use with simple web services interface to store and retrieve any amount of data from anywhere on the web
- data is spread across multiple devices and facilities enabling fault scenario

## Basics
- object-based - allows file upload
- file size allowance, 0Byte to 5TB
- unlimited storage
- files are stored in Buckets (similar to a folder)
- S3 is a universal namespace; names must be unique globally
- URL Parse - https://s3-eu-west-1.amazonaws.com/acloudguru
  - s3 - product used
  - eu-west-1 - region-location-box
  - amazonaws.com - domain service
  - acloudguru - unique bucket namespace
- when you upload a file to S3, you will receive a HTTP 200 code if the upload was successful
  - this code will only be seen if you are uploading using the API or the CLI

## Data Consistency Model for S3
- Read after Write consistency for PUTs of new objects
  - file is immediately accessible after upload
- eventual consistency for overwrite PUTs and DELETEs; can take some time to propagate
- modifications of deletion of a file will take time to register

## S3 is a Simple Key-Value Store
- key - the name of the object
- value - the data, which is made up of a sequence of bytes
- Version ID - important for versioning
- Metadata - data about data you are strong
- Sub-resrouces - bucket-specific configuration
  - bucket policies & access control lists
  - cross origin resource sharing (CORS)
  - transfer acceleration - a feature from AWS to upload files faster

## S3 Features
- built for 99.99% availability for the S3 platform
- Amazon guarantees 99.9% availability
- Amazon guarantees 99.999999999% durability for S3 information (11 x 9s)
- tiered storage available
- lifecycle management
- versioning
- encryption
- secure your data - access control lists and bucket policies

## Storage Tiers/Classes
- S3
  - availability: 99.99%
  - durability: 99.999999999%
  - stored redundantly across multiple devices in multiple facilities
  - designed to sustain the loss of 2 data centers of facilities concurrently
- S3 Infrequently Accessed (IA)
  - for data that is accessed less frequently
  - requires access when needed
  - lower fee than S3
  - charge a retrieval fee
- S3 One Zone IA
  - same as IA, however data is stored in a single Availability Zone only,
  - availability: 99.5%
  - durability: 99.999999999%
  - 20% less cost than S3 IA
- Reduced Redundancy Storage
  - availability: 99.99% over a given year
  - durability: 99.99% over a given year
  - used for data that can be recreated if lost -- like thumbnails
  - this is disappearing from AWS documentation but may still feature in the exam
- Glacier
  - very cheap
  - archival only
  - optimized for data that is infrequently accessed and it takes 3 - 5 hours to restore from Glacier
  - no real-time access

## Cost/Charge Rates
- Charge for:
  - storage per GB
  - requests (GET, PUT, COPY, etc.)
  - storage management pricing
    - inventory, analytics and object tags
  - data management pricing
    - data transferred out of S3
  - transfer acceleration
    - use of CloudFront to optimize transfers

## Exam Tips
- object-based storage for files
- not suitable to install an operating system or running a database on
- files can be from 0Bytes to 5TB
- unlimited storage
- files stored in Buckets
- S3 is a universal namespace; names must be unique globally
- Read after Write consistency for PUTs of new objects
- eventual consistency for overwrite PUTs and DELETEs; can take some time to propagate
- Storage Classes/Tiers
  - S3 - durable, immediately available, frequently accessed
  - S3 IA - durable, immediately available, infrequently accessed
  - S3 One Zone IA - same as IA, but data is stored in a singl Availability Zone only
  - S3 Reduced Redundancy Storage - data that is easily reproducible such as thumbnails
  - Glaciers - archived data, where you can wait 3 - 5 hours before accesssing
- S3 Object Core Fundamentals
  - key (name)
  - value (data)
  - version ID
  - metadata
  - sub-resrouces - bucket-specific configuration
    - bucket policies
    - access control ists
    - cross origin resource sharing (CORS)
    - transfer acceleration
- successful upload s will generate a HTTP 200 status code -- when using the API or CLI
- make sure to read the [S3 FAQ](https://aws.amazon.com/s3/faqs/)