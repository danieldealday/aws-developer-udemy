# Scan Versus Query API Call

## Query
- a query operation finds items in a table based on the Primary Key attribute and a distinct value to search for e.g. select an item where the User ID is equal to 212, will select all the attributes for that item, like first name, surname, email etc.
- use an optional Sort Key name and value to refine the results e.g. if your Sort Key is a timestamp, you can refine the query to only select items with a timestamp of the last 7 days
- by default, a Query returns all the attributes for the items but you can use the ProjectionExpression paramenter if you want e.g. if you only want to see the email address rather than all the attributes
- results are always sorted by the Sort Key
- Numeric order - by default in ascending order (1, 2, 3, 4)
- ASCII character code values
- you can revers the order by setting the ScanIndexForward parameter to `false`
- by default, Queries are Eventually Consistent
- you need to explicitly set the query to be Strongly Consistent
