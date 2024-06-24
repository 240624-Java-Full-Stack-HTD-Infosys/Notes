# Querying Documents
We can query our database for information in a number of different ways. In these notes we will show syntax for both mongosh and Java. We will cover several basic query examples.

## Query Operators
There are a number of operators to use when querying. Take a look at this simple SQL query:

```SQL
SELECT * FROM things 
WHERE col1 = 'value1' 
AND col2 > '100';
```
Here we are only going to get rows which have `value1` in the `col1` column, and have a value greater than `100` in `col2`. An equivalent query in mongosh could look like this:

```sh
db.things.find({col1: {$eq: "value1"}, col2: {$gt: 100}})
```

Here we see the `$eq` and `$gt` operators which specify equality and greater than. We are also implicitly using a logical AND here. We could re-write this to use the `$and` operator:

```sh
db.things.find({$and [{col1: {$eq: "value1"}}, {col2: {$gt: 100}}]})
```
Note that the `$and` operator expects an array of conditions.

Let's see an example of this in Java:
```Java
findIterable = collection.find(and(eq("col1", "value1"), gt("col2", 100)));
```

### List of Query Operators
This list is just a few common operators. The complete list can be found in the [mongo docs](https://www.mongodb.com/docs/manual/reference/operator/query/#std-label-query-selectors).

#### Comparison Operators:
 - eq - equality
 - ne - not equal
 - gt - greater than
 - gte - greater than or equal to
 - lt - less than
 - lte - less than or equal to
 - in - matching any value in given array
 - nin - not matching any value in given array

#### Logical Operators:
 - and - joins clauses, results match all conditions
 - or - joins clauses, results match one or more conditions
 - nor - joins clauses, results match none of the conditions
 - not - inverts the logic of a query expression, results do not match conditions



