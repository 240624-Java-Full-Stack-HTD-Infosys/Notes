# Multiplicity Relationships
In a relational database foreign keys allow us to set up "relations" between tables. We can [emulate](https://www.mongodb.com/docs/manual/applications/data-models-relationships/) this behavior somewhat in MongoDB with **embedded documents** and **document references**.

#### Embedded Data
A document is a series of key/value pairs formatted as BSON. The values can be of many types, including more BSON objects. This effectively means that a document can "embed" all of the same data as another document. Consider this example:

```JSON
{
  _id: "abcefg123",
  type: "Customer",
  identity: {
    firstName: "John",
	lastName: "Doe"   
  },
  address: {
    street: "21 Circle st.",
    city: "Albany",
    state: "NY",
    zip: "12345"
  }
}
```
We have our document which contains four fields (key/value pairs), `_id`, `type`, and `identity`, and `address`. `identity` and `address` are also BSON objects. In a relational database this one-to-one relation of identity to address might be designed with two tables which reference eachother. Here we have embedded this data into a single document which represents the entire relation. In a document database like MongoDB, instead of keeping this data separate and joining it back together in query, we can group all this data together. We're interested in the totality of the data, which represents a customer with an identity and an address, so it makes sense that this data is contained in a single document.

#### Document References
For a pattern similar to foreign key relations between tables, we can reference documents to create a relation between collections. It's important to note that MongoDB doesn't enforce referential integrity. There is no mechanism to protect a reference from being orphaned like there is in a relational database. 

We can take the above example and create several interconnected collections.

Here is our customer:
```JSON
{
    _id: "abcefg123",
    type: "Customer",
    identity_id: "1f3f5f220",
    address_id: "ef56e2aba"
}
```
`identity_id` above references the value of `_id` in the identity collection:
```JSON
{
    _id: "1f3f5f220",
    firstName: "John",
	lastName: "Doe"   
},
```
And `address_id` above references the `_id` field in the address collection:
```JSON
{
    _id: "ef56e2aba",
    street: "21 Circle st.",
    city: "Albany",
    state: "NY",
    zip: "12345"
}
```

### Embed vs. Reference
The fewer documents we have to search through the better our performance will be. In this way embedding data can result in better search times when querying the database. However, embedding data often leads to duplicating data which can be problematic if that data needs to get updated frequently.

Consider embedding when:
 - One document would "contain" another
 - You need excellent performance on reads
 - The data is frequently consumed as a whole

Consider references when:
 - Embedding would duplicate the data
 - The data frequently changes
 - You have complex many-to-many relations
 - Part of the data is frequently consumed on its own

### Modeling Multiplicity Relations

#### One-to-One with Embedded Data
This is exactly what we had above, where a customer has only one identity and only one address. In this example we will write it slightly differently, but it amounts to the same thing.
```JSON
{
    _id: "65d7721f9b76f97a27544819",
    firstName: "John",
    lastName: "Doe",
    address: {
        street: "21 Circle st.",
        city: "Albany",
        state: "NY",
        zip: "12345"
    }
}
```

#### One-to-Many with Embedded Data
Let's say our customers might have multiple addresses. We can simply have an array of addresses embedded to establish a one-to-many relation:

```JSON
{
    _id: "65d7721f9b76f97a27544819",
    firstName: "John",
    lastName: "Doe",
    address: [
        {
            street: "21 Circle st.",
            city: "Albany",
            state: "NY",
            zip: "12345"
        },
        {
            street: "1 way st.",
            city: "Anaheim",
            state: "CA",
            zip: "98765"
        } 
    ]
}
```

#### One-to-Many with Document References
Let's "normalize" the data above by moving the addresses into their own collection, and re-establishing the one-to-many relation using references:

```JSON
{
    _id: "65d7721f9b76f97a27544819",
    firstName: "John",
    lastName: "Doe",
    address_id:[
        "b76f97a2754481a65d7721f9",
        "f9b76f97a26772175445a81b"
    ]
}
```
Both of those address ids reference documents found in the addresses collection:
```JSON
{
    _id: "b76f97a2754481a65d7721f9",
    street: "21 Circle st.",
    city: "Albany",
    state: "NY",
    zip: "12345"
}
```
```JSON
{
    _id: "f9b76f97a26772175445a81b",
    street: "1 way st.",
    city: "Anaheim",
    state: "CA",
    zip: "98765"
}
```

#### Many-to-Many with Document References
Let's consider a case where we have a complex many-to-many relation: students and teachers. Students may take any number of classes and may have 0, 1, or more teachers. Teachers, similarly, may teach many classes and may have 0, 1, or more students. References are best suited to this use case. In a relational database we would likely have a junction table to establish these connections. Here we will have a third collection, classes, which links teachers to students.

#### Teachers:
```JSON
{
    _id: "aaabbbccc123",
    teacher: "Mr. Paulson"
}
```
```JSON
{
    _id: "xxxyyyzzz321",
    teacher: "Mrs. Chevapravatdumrong"
}
```

#### Students:
```JSON
{
    _id: "1112223334445",
    student: "Mary Smith",
    grade: "freshman"
}
```
```JSON
{
    _id: "5556667778889",
    student: "John Doe",
    grade: "junior"
}
```
```JSON
{
    _id: "0005552228886",
    student: "Larry Potter",
    grade: "senior"
}
```

#### Classes:
```JSON
{
    _id: "9b76f97a275412d77226481c",
    class: "Physics 101",
    teacher: "aaabbbccc123",
    students: [
        "5556667778889",
        "0005552228886"
    ]
}
```
```JSON
{
    _id: "12d3768781cb76f97a27ab52",
    class: "Physics 205",
    teacher: "aaabbbccc123",
    students: [
        "1112223334445"
    ]
}
```

```JSON
{
    _id: "65d777e520aca6b8a776323e",
    class: "Western Civ",
    teacher: "xxxyyyzzz321",
    students: [
        "1112223334445",
        "0005552228886"
    ]
}
```