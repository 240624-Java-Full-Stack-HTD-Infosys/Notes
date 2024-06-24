# MongoDB Overview
MongoDB is an open-source NoSQL document database. It is designed for ease-of-use and maximum flexibility. Mongo stores data in the form of BSON documents instead of the rows and columns of traditional SQL or relational databases. MongoDB offers drivers for many popular programming languages including Java, C/C++, Python, and Typescript to name a few. 

### Document Storage
Instead of rows, each record in a Mongo database is stored as a **document**. A document is filled with BSON formatted data in key/value pairs. These documents are then grouped together into **collections**. 

### BSON
BSON means Binary Javascript Object Notation. A BSON object is a binary serialization of a JSON object, which is how BSON gets its name (Binary javaScript Object Notation). BSON mostly adheres to the JSON standard, but extends it with new data types. We will show BSON in a human-readable format that looks exactly like JSON.

Like JSON, BSON objects are made up of key/value pairs, where the keys are strings and the values can be many types including strings, integers, arrays, and even other BSON objects. 

### Indexes
Querying a collection based on some data in that collection, for instance searching a list of customers for a name, would normally require scanning every document in the collection. This is hardly ideal, so we have **Indexes**. Adding an index to a collection will make querying that collection based on the indexed field much quicker. MongoDB will create a [B-Tree](https://en.wikipedia.org/wiki/B-tree) where it will store some portion of the collection that can be quickly searched. Once the index has been searched, the rest of the data can be pulled from the matching documents.

### Primary Keys
Every document is given an `_id` field which acts as a dedicated primary key. This field is automatically indexed, and uniqueness is enforced. While we can index and enforce uniqueness on other fields, we can't really specify a different primary key on a collection.

### Foreign Keys & Referential Integrity
Referential Integrity isn't really supported by MongoDB, nor are foreign keys. There are ways to emulate some concepts like this, but there are no constraints which would directly stop you from removing a dependent document. For instance, we can reference

There is a tool, [Relational Migrator](https://www.mongodb.com/docs/relational-migrator/) which is used to translate relational database schema into MongoDB schema. This tool can help you create "synthetic foreign keys". We will not be getting into that.