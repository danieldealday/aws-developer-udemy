# RDS - Backups, Multi-AZ and Read Replicas
- Back Up Types
  - automated
  - database snapshots

## Automated Backups
- allow you to recover your database to any point in time within a "retention period"
- retention period can be between 1-to-35 days
- takes a daily snapshot and will also store transaction logs through the day
- during a recovery, AWS will choose the most recent daily back up and apply transaction logs relevant to that day allowing point-in-time recovery down to a second within the retention period
- enabled by default
- backup data is stored in AWS S3 service and fress storage space equal to the size of your database
  - example: if you have RDS instance of 10Gb,then you have 10Gb worth of storage
- backups are taken within a defined window
- during the backup windows, storage input/output may be suspended while your data is being backed up and you may experience elevated latency

## Snapshots
- performed manually
- stored even after you delete the original RDS instance, unlike autoated backups

## Restoring Backups
- when you restor either an Automated Backup or a manual Snapshot, the restored version of the database will be a new RDS instance with a new DNS endpoint

## Encryption
- encrypting data at rest is supported for...
  - MySQL
  - Oracle
  - SQL Server
  - PostgreSQL
  - MariaDB
  - Aurora
- encryption is done by AWS Key Management Service (KMS)
- once RDS is encrypted, it includes data at rest, automated backups, read replicas, and snapshots
- encrypting an existing database instance is not supported
- to encrypt an existing databse, first create a snapshot, make a copy of that snapshot, and then encrypt the copy

## Multi-AZ
- synchronous
- allows you to have an exact copy of your production database in another availability zone 
- when your production database is written to the write action is synchronously copied to the standby database
- useful scenarios
  - database maintenance
  - database failure
  - availability zone failure
- SQL Server, Oracle, MySQL Server, PostgreSQL, MariaDB

## Read Replica
- allow you to have a read-only copy of your production database achieved through asynchronous replication from  the primary RDS instance to the read replica
- primarly used for read-heavy database workloads
- used to relieve load from the primary production database
- able to have read replica of a read replica; there will be some replication latency
- use read replicas to scale out
- MySQL Server, PostgreSQL, MariaDB, Aurora
- not for disaster recovery
- must have automatic backups turned on in order to deploy a read replica
- you can have up to 5 read replica copies of any database
- each read replica will have its own DNS end point
- able to have read replicas that have Multi-AZ
- read replicas can be promoted to be their own databases; this breaks the replication