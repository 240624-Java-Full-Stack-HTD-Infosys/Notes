# Documents
MongoDB stores data as BSON documents (JSON with [extra specifications](https://bsonspec.org/)). This structure is simple and flexible. Here is an example document from the MongoDB [documentation](https://www.mongodb.com/docs/v7.0/core/document/). Let's call this a user:

```JSON
{
    name: "sue",
    age: 26,
    status: "A",
    groups: ["news", "sports"]
}
```

With BSON, just like JSON, we have a series of key/value pairs. Keys are strings, values can be many different types including other BSON objects or arrays. In this example `groups` contains an array of strings. Below is another example with a nested BSON object:

```JSON
{
    name: "sue",
    age: 26,
    status: "A",
    groups: ["news", "sports"],
    address: {
        street: "21 abc st.",
        city: "Albany",
        state: "NY",
        zip: "12345"
    }
}
```

`address` contains another BSON object. This is called nesting. The address object is nested within this user object.

### Embedded Documents
Because a document is a BSON object, and BSON objects can contain other BSON objects, we can "nest" or "embed" a whole document within another. We can use this to model some multiplicity relations. This is something we will see in greater detail later. In the last example, we have effectively embedded an `address` document within the user document.

### Dot Notation - Arrays
Similar to the Java syntax to de-reference an object and gain access to its members, we use dot notation to access nested objects or elements within arrays. In the example above we have the `groups` array. If we wanted to access the value `"sports"` we would use dot notation like this: `groups.1`. (Remember that arrays are 0-indexed in nearly every language and implementation).

Here is an example using mongo shell.

Add a couple documents to a collection which contain arrays with values:
```sh
db.arrays.insertMany([
  {array: ['zero', 'one', 'two']},
  {array: ['three', 'four', 'five']},
  {array: ['six', 'seven', 'eight']}
])
```
Now let's query for the record which contains the element "four" in the 1st index position.

```sh
db.arrays.find({'array.1': "four"})
```

### Dot Notation - Documents
We can also use dot notation to access nested documents. 

```sh
db.embeds.insertMany([
  {name: "Kyle", info: {age: 38, favColor: 'blue'}},
  {name: "John", info: {age: 22, favColor: 'red'}},
  {name: "Alison", info: {age: 33, favColor: 'yellow'}}
])
```

Now let's find the document in which the embedded document contains an `age` value of `38`:
```sh
db.embeds.find({'info.age': 38})
```