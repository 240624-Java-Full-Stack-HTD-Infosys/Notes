# Aggregation
Much like in SQL databases, we often want to aggregate the data to analyze it. There are some simple single purpose aggregation methods in MongoDB such as `countDocuments()`, but most of the aggregation is done with aggregation pipelines.

### Single Purpose Methods
The [MongoDB docs](https://www.mongodb.com/docs/manual/aggregation/) list 3 single purpose methods:
 - `count()` (See also: `countDocuments()`) - returns the number of documents in a collection
 - `estimatedDocumentCount()` - returns an estimate of the count of documents in a colelction
 - `distinct()` - returns an array of distinct values found for some field in a collection

The first one, `count()` is actually depricated in favor of `countDocuments()`. 

### Aggregation Pipelines
An aggregation pipeline consists of one or more stages which perform operations on the data. After one stage, the data is then passed to the next stage for more manipulation. Finally, when all stages are complete, we will get our aggregate results.

We start a pipeline by calling the `db.orders.aggregate()` method. We pass an array to this method, where each element in the array is a stage. These stages are executed in order as they appear in the array. Let's take a look at an example from the [MongoDB docs](https://www.mongodb.com/docs/manual/core/aggregation-pipeline/):

First we create a collection and add some records. These are pizza orders one could place at a restaurant.
```sh
db.orders.insertMany( [
   { _id: 0, name: "Pepperoni", size: "small", price: 19,
     quantity: 10, date: ISODate( "2021-03-13T08:14:30Z" ) },
   { _id: 1, name: "Pepperoni", size: "medium", price: 20,
     quantity: 20, date : ISODate( "2021-03-13T09:13:24Z" ) },
   { _id: 2, name: "Pepperoni", size: "large", price: 21,
     quantity: 30, date : ISODate( "2021-03-17T09:22:12Z" ) },
   { _id: 3, name: "Cheese", size: "small", price: 12,
     quantity: 15, date : ISODate( "2021-03-13T11:21:39.736Z" ) },
   { _id: 4, name: "Cheese", size: "medium", price: 13,
     quantity:50, date : ISODate( "2022-01-12T21:23:13.331Z" ) },
   { _id: 5, name: "Cheese", size: "large", price: 14,
     quantity: 10, date : ISODate( "2022-01-12T05:08:13Z" ) },
   { _id: 6, name: "Vegan", size: "small", price: 17,
     quantity: 10, date : ISODate( "2021-01-13T05:08:13Z" ) },
   { _id: 7, name: "Vegan", size: "medium", price: 18,
     quantity: 10, date : ISODate( "2021-01-13T05:10:13Z" ) }
] )
```

Now let's aggregate some data from this colleciton:

```sh
db.orders.aggregate([
   {$match: { size: "medium" }},
   {$group: { _id: "$name", totalQuantity: { $sum: "$quantity" }}}
])
```
In the first phase we match values. This is like the `WHERE` clause in SQL. In this example we are matching only those pizzas which have a size of "medium". There are three orders in the collection which are size medium, and those matching records are passed to the next phase.

In the second phase we are grouping the results. This is similar to `GROUP BY` in SQL. We are first grouping by name, then summing all the quantities that are in the group. Note the `$` prefix on the values here, we prefix a field name with the dollar sign whenever we are providing the field as a value. In our results we will get objects with an `_id` which matches the grouped `name` field. These will contain a `totalQuantity` which is the sum of all quantities in the group.

Here are the results:
```sh
[
  { _id: 'Vegan', totalQuantity: 10 },
  { _id: 'Pepperoni', totalQuantity: 20 },
  { _id: 'Cheese', totalQuantity: 50 }
]
```
So we are only considering medium size pizzas, we had a total quantity of 10 medium vegan pizzas, 20 medium pepperoni, and 50 medium cheese.

There are a great number of commands, stages, operators, and more in the [documentation](https://www.mongodb.com/docs/manual/reference/aggregation/) which we will not cover in detail.