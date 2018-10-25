# Scan Vs. Query API Call

## Query
- is an operation that finds items in a table based on the Primary Key and distinct value to search for e.g. select an item where the user ID is equal to 212, will select all the attributes for that item
- use an optional sort key name and value to refne the results e.g. if your sort key is a timestamp, you can refine the query to only select items with a timestamp of the last 7 days
- by default, a query returns all the attributes for the items but you can use the ProjectionExpression parameter if you want the query to only return the specific attributes you want e.g. if you only want to see the email address rather than all the attributes
- results are always sorted by the sort key
- numeric order - by default in ascending order
- ASCII character code values
- you can reverse the order by setting the ScanIndexForward parameter to false
- by default. queries are eventually consistent
- you need to explicitly set the query to be Strongly Consistent

## Scan
- an operation examines every item in the table
- by default, returns all data attributes
- use the ProjectionExpression parameter to refine the scan to only return the attributes you want

## Query & Scan Comparison
- query is more efficient than a scan
- scan dumps the entire table, then filters out the values to provide the desired result - removing the unwanted data
- this adds an extra step of removing the data you don't want
- as the table grows, the scan operation takes longer
- scan operation on a large table can use up the provisioned throughput for a large table in just a single operation

## Performance Improvement Techniques
- you can reduce the impact of a query or scan by setting a smaller page size which uses fewer read oeprations e.g. set the page size to return 40 times
- larger number of smaller operatinos will allow other requests to succeed without throttling
- avoid using scan operations if you can: design tables in a way that you can use the Query, Get or BatchGetItem APIs
- by default, a scan operation processes data sequentially in returning 1MB increments before moving on to retrieve the next 1MB of data; it can only scan one partition at a time
- you can configure DynamoDB to use Parallel scans instead by logically dividing a table or index into segments and scanning each segment in parallel
- best to avoid parallel scans if your table or index is already incurring heavy read/write activity from other applications

## Tips
- a query operation finds items in a table using only the primary key attribute
- yo provide the primary key name and a distinct value to search for
- a scan operation examines every item in the table
- by default, returns all data attributes
- use the ProjectionExpression parameter to refine the results
- query results are always sorted by the sort key is there one
- sorted in ascending order
- set ScanIndexForward parameter to `false` to reverse the order - queries only
- query operation is generally more efficient than a scan
- reduce the impact of a query or a scan by setting a smaller page size which uses fewer read operations
- isolate scan oeprations to specific tables and segregate them from your mission-critical traffic
- try Parallel Scans, rather than the default sequential scan
- avoid using scan operations if you can: design tables in a way that you can use the Query, Get or BatchGetItem APIs