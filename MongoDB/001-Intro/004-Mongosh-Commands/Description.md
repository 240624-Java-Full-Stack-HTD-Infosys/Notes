# Mongo Shell Command Cheat Sheet

### Add user
```sh
db.createUser({
    user: "newUser",
    pwd: "newPass123",
    roles: ["readWrite", "dbAdmin"]
})
```

### Remove User
```sh
db.dropUser("newUser")
```

### Authenticate
```sh
db.auth("username", "password")
```

### Create Index
```sh
db.customers.createIndex(
    {
        "firstName": 1,
        "lastName": 1
    },
    {
        unique: true
    }
)
```

### Insert Document
```sh
db.customers.insertOne({
    firstName: "John",
    lastName: "Smith"
})
```

### Insert Documents
```sh
db.customers.insertMany([
    {firstName: "David", lastName: "Wilson"},
    {firstName: "Jack", lastName: "Wilson"},
    {firstName: "Tony", lastName: "Wilson"}
])
```
