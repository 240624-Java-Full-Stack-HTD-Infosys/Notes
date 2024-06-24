# MongoDB Transactions
One main purpose of transactions in databases is to make operations atomic, that is all the work is applied in one single uninturuptable operation. If there is any problem, none of the work is applied and the database remains in the state it was in. There are other attributes to transactions like isolation and propagation, but we won't be considering those here. Research [ACID](https://en.wikipedia.org/wiki/ACID) to learn more.

Consider the case where we are adding 5% interest to every balance in a bank's database. It gets half way through before failing for some reason. Without a transaction, it can be difficult to fix this situation. With a transaction, the work that had been done before the failure should get rolled back. If the full amount of work succeeded, only then are those changes "committed" to the database. Making the changes isn't atomic, but we make them to a temporary location and when ready we simply apply that temporary state to make it permenant in one uninturptable operation.

For the most part in MongoDB we don't need to worry about transactions. This is because of the document structure. For the most part, changing a single record means only changing a single document and these operations are already atomic by design. MongoDB docs say:

    "In MongoDB, an operation on a single document is atomic. Because you can use embedded documents and arrays to capture relationships between data in a single document structure instead of normalizing across multiple documents and collections, this single-document atomicity obviates the need for distributed transactions for many practical use cases.
    
    For situations that require atomicity of reads and writes to multiple documents (in a single or multiple collections), MongoDB supports distributed transactions. With distributed transactions, transactions can be used across multiple operations, collections, databases, documents, and shards."

So we may need transactions when making multiple reads and writes to multiple documents.

Note: Our database is probably not set up to handle transactions. If you want to get hands-on experience with this, research how to [convert](https://www.mongodb.com/docs/manual/tutorial/convert-standalone-to-replica-set/) a standalone database into a replica set.

## Java Example
In this example we will use a transaction to insert multiple records in a single atomic operation.

We start by creating our `MongoClient` and `ClientSession` references.
```Java
final MongoClient client = MongoClients.create(uri);

final ClientSession clientSession = client.startSession();
```

Optionally we can create a `TransactionOptions` object to configure the transaction. This will be used when we call `withTransaction()` later.
```Java
TransactionOptions txnOptions = TransactionOptions.builder()
        .readPreference(ReadPreference.primary())
        .readConcern(ReadConcern.LOCAL)
        .writeConcern(WriteConcern.MAJORITY)
        .build();
```

Here is where we define the transaction itself. If you haven't seen something like this before, this is an ad-hoc class definition. We are creating a new `TransactionBody` object, wrapped around a `String`. The `execute()` method we define will contain the work we want the transaction to complete. We simply apply the work like normal, then return a message.
```Java
TransactionBody txnBody = new TransactionBody<String>() {
    public String execute() {
        MongoCollection<Document> coll1 = client.getDatabase("mydb1").getCollection("foo");
        MongoCollection<Document> coll2 = client.getDatabase("mydb2").getCollection("bar");
        /*
           Important:: You must pass the session to the operations.
         */
        coll1.insertOne(clientSession, new Document("abc", 1));
        coll2.insertOne(clientSession, new Document("xyz", 999));
        return "Inserted into collections in different databases";
    }
};
```

And here we finish the process by calling `withTransaction()` and passing our defined transaction body and options. When we are done, in the `finally` block we close out the session.
```Java
try {
    clientSession.withTransaction(txnBody, txnOptions);
} catch (RuntimeException e) {
    e.printStackTrace();
} finally {
    clientSession.close();
}
```