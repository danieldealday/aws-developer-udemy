# Introduction to DynamoDB
- a fast and flexible NoSQL database service for all applications that need consistent, single-digit millisecond latency at any scale
- a fully managed database and supports both document and key-value data models
- its flexible data model and reliable performance make it a great fit for mobile, web, gaming, ad-tech, internet-of-things and many other applications

## Characteristics
- stored on Solid State Drive (SSD) storage
- spread across 3 geographically distinct data centers
- choice of 2 consistency models:
  - eventual consistent reads (default)
  - strongly consistent reads

## Consistency Models
- Eventual Consistent Reads
  - consistency across all copies of data is usually reached within a second; repeating a read after a short time should return the updated data (best read performance)
- Strongly Consistent Reads
  - a strongly consistent read returns a result that reflects all writes that received a successful response prior to the read

## Data Organization
- tables
- items (think a row of data in a table)
- attributes (think of a column of data in a table)
- supports key-value and document data structures
- key = name of the data; value = the data itself
- documents can be written in JSON, HTML or XML

## Primary Keys
- DynamoDB stores and retrieves data based on a Primary Key
- 2 types of Primary Key
- Partition Key - unique attribute e.g. user ID
- value of the partition key is input to an internal hash function which determines the partition or physical location on which the data is stored
- if you are using the partition key as your primary key, then no 2 items can have the same partition key
- Composite Key (Partition Key + Sort Key) in combination e.g. same user posting multiple time to a forum
  - primary key would a composite key consisting of:
    - parition key - user id
    - sort key - timestamp of the post
    - 2 items may have the same partition key, but they must have a different sort key
    - all items with the same partition key are stored together, then sorted according to the sort key value
    - allows you to store multiple items with the same partition key
    ```javascript
    {
      'UniqueID': 1975, // Partition Key
      'FirstName': 'Allan',
      'Surname': 'Brown',
      'Phone': '555-2323'
    
    },
    {
      'UniqueID': 1976, // Partition Key
      'FirstName': "Riad',
      'Surname': 'Ramanov',
      'CourseName': 'AWS_Developer_Associate', // Sort Key
      'Address': '{
        'Number': '5',
        'Street': 'River Road
      }'
    }
    ```
## Access Control
- authentication and access control to DynamoDB is managed via AWS IAM
- you can create an IAM user within you AWS account which has specific permissions to access and create DynamoDB tables
- you can create an IAM role which enables you to obtain temporary access keys that can be used to access AWS services like DynamoDB
- you can also use speciall IAM Condition to restrict user access to only their own records
  - Example:
    - imagine a mobile gaming application with millions of users
    - users need to access the high scores for each game they are playing
    - access must be srestricted to ensure they cannot view anyone else's data
    - this can be done by adding a Condition to an IAM Policy to allow access only to items where the Partition Key value mathces their User ID
    ```javascript
    'Sid': 'AllowAccessToOnlyItemsMatchingUserID', // statement identifier
    'Effect': 'Allow",
    'Action': [ // defines the actinos that the policy allows
      'dynamodb:GetItem",
      'dynamodb:PutItem",
      'dynamodb:UpdateItem",
    ],
    'Resource' : [
      'arn:aws:dynamodb:eu-west-1:123456789012:table/HighScores'
    ],
    'Condition' : {
      'ForAllValues:StringEquals' : {
        'dynamodb:LeadingKeys': [ // allows users to access only the items where the partition key value matches their user id
          '${www.mygame.com:user_id}'
        ],
        'dynamodb:Attributes': [ // defines the attributes that the policy applies to
          'UserId',
          'GameTitle',
          'TopScore'
        ]
      }
    },
    ```

## Tips
- Amazon DynamoDB is a low latency NoSQL database
- consists of Tables, Items and Attributes
- supports both document and key-value data models
- supported document formats are JSON, HTML and XML
- 2 types of Primary Key - `Partition Key` and a combination of `Partition Key + Sort Key` (Composite Key)
- 2 consistency models: strongly consistent / eventually consistent
- access is controlled using IAM policies
- fine grained access control using IAM Condition parameter: `dynamodb:LeadingKeys` to allow users to access only the items where the partition key value matches their user ID