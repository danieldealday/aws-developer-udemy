# Indexes
- in SQL databases, an index is a data structure which allows you to perform fast queries on specific columns in a table; you select the columns that you want included in the index and run your searches on the index - rather than on the entire dataset
- in DynamoDB, 2 types of index are supported to help speed up your DynamoDB queries
  - local secondary index
  - global secondary index

## Local Secondary Index
- can only be created when you are creating your table
- you cannot add, remove or modify it later
- it has the same partition key as your original table but a different sort key
- gives you a different view of your data, organized according to an alternative sort key
- any quereies based on this sort key are much faster using the index than the main table
  - example:
    - Partition Key : User ID
    - Sort Key : account creation date

## Global Secondary Index
- you can create when you create your table or add it later
- different partition key as well as a different sort key so it gives a completely different view of the data
- speed up any queries relating to this alternative parition and sort key
- e.g. Partition Key: email address; Sort Key: last login date

## Tips
- indexes enable fast queries on specific data columns
- give you a different view of your data, based on a alternative partition/sort keys
- important to understand the difference
  - local secondary index
    - must be created at when you create your table
    - same partition key as your table
    - different sort key
  - global secondary index
    - can create any time - at table creation or after
    - differnt partition key
    - different sort key