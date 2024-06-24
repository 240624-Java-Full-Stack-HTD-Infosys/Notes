# Indexes
Indexes exist to spead up the location of information. An index in MongoDB is [B-Tree](https://en.wikipedia.org/wiki/B-tree) data structure which contains some portion of the collection's data. This tree is very quick to traverse, so searching for some information in the index is far superior to scanning through a whole collection. The index will contain values from one or more fields in the collection, and will mantain its own sorting.

#### Index Types
 - Single Field - The simpliest example, sort data based on the value of a single field
 - Compound - Index based on 2 or more fields, and sorted by grouping the first field, followed by each subsequent field in order.
 - Multikey - Automatically used when you index on a field which contains an array. Document may be referenced multiple times within the index as all array values are present.
 - Geospacial - A special index intended for use with geospacial coordinates
 - Text - Index on string fields which supports text search queries
 - Hashed - Index based on hashing the values of indexed fields
 - Clustered - Index for clustered collections

#### Index Properties
 - Case-insensitive - support indexing strings without regard to case.
 - Hidden - Inactive but not dropped, can be un-hidden easily. Index is fully maintained while hidden.
 - Partial - only indexes documents where the indexed field meets some constraint.
 - Sparse - only indexes documents which contain the indexed field
 - TTL (Time To Live) - only keeps index entries for a specified amount of time, effectively an index of the "newest" documents.
 - Unique - constrains the indexed field to be unique. Duplicate entries will be rejected.

### Default Index
Every collection has a default index on the `_id` field. This index cannot be dropped, and enforces uniqueness of the primary key.

### Sorting
Documents in a MongoDB are sorted according indexes, and without adding any additional indexes they are sorted based on the `_id` field. If you routinely want results to be in a sorted order based on another field, you will want to index that field. 

Every index has a sorting property which indicates if it should be ordered ascending or descending. When an index is created the indexed columns are listed as keys, and they are given values of `1` or `-1` to indicate ascending or descending.

In the below example we create an index on the `customers` collection which will keep the index sorted by `name` in ascending order:
```sh
db.customers.createIndex({name: 1})
```

### Strategies
There is no single guiding rule about what indexes are used where and with which properties. Our indexes should be designed with our needs in mind. The most important factor is how you will be querying the data. MongoDB documentation gives us the following guidance:
 - [The ESR (Equality, Sort, Range) Rule](https://www.mongodb.com/docs/manual/tutorial/equality-sort-range-rule/#std-label-esr-indexing-rule)
 - [Create Indexes to Support Queries](https://www.mongodb.com/docs/manual/tutorial/create-indexes-to-support-queries/#std-label-create-indexes-to-support-queries)
 - [Use Indexes for Sorting](https://www.mongodb.com/docs/manual/tutorial/sort-results-with-indexes/#std-label-sorting-with-indexes)
 - [Indexes Should Fit in RAM](https://www.mongodb.com/docs/manual/tutorial/ensure-indexes-fit-ram/#std-label-indexes-ensure-indexes-fit-ram)
 - [Query Selectively](https://www.mongodb.com/docs/manual/tutorial/create-queries-that-ensure-selectivity/#std-label-index-selectivity)