# *🥭MongoDB CRUD Operation*

## *✔️ CRUD operations create, read, update, and delete documents*

### *🔥 Create Operations*

### 🪄 Creating a New Database
```javascript
use userdb;
```
Output 
> switched to db userdb

*Note :- In MongoDB, a database is not actually created until it has atleast one collection !*

### 🪄 Creating Collection

Method 1 : Creating Empty Collection
```Javascript
db.createCollection("posts")
show collections
```

Method 2 : creating a collection during the insert process
```Javascript
db.posts.insertOne({"title": "Post 1"})
```

Output:
```javascript
userdb> show collections
posts
```
### 🪄 Creating Documents
*There are two ways to create new documents to a collection*
1. insertOne():
```javascript
db.users.insertOne({ name: "Angela", age: 27 });
```
Output :
```javascript
{
  acknowledged: true,
  insertedId: ObjectId('65e22ff7dcee93f570585704')
}
```

2. insertMany():
```javascript
db.users.insertMany([{name: "User1", age: 22}, {name: "User2", age: 25}])
```

Output:
```javascript
{
  acknowledged: true,
  insertedIds: {
    '0': ObjectId('65e230e0dcee93f570585708'),
    '1': ObjectId('65e230e0dcee93f570585709')
  }
}
```

### *🔥 Read Operations*
1. Read All the Documents
```javascript
db.users.find()
```

output:
```javascript
[
  {
    _id: ObjectId('65e23306dcee93f57058570f'),
    name: 'User1',
    age: 22,
    city: 'Mumbai'
  },
  {
    _id: ObjectId('65e23306dcee93f570585710'),
    name: 'User1',
    age: 25,
    city: 'Pune'
  },
  {
    _id: ObjectId('65e23306dcee93f570585711'),
    name: 'User2',
    age: 30,
    city: 'Kalyan'
  }
]
```

2. Read Document with specific query

*Getting the document where name is "User1"*
```javascript
db.users.find({name: "User1"})
```

output:
```javascript
[
  {
    _id: ObjectId('65e23306dcee93f57058570f'),
    name: 'User1',
    age: 22,
    city: 'Mumbai'
  },
  {
    _id: ObjectId('65e23306dcee93f570585710'),
    name: 'User1',
    age: 25,
    city: 'Pune'
  }
]
```
3. Read Document with query & projection

*Hiding files id and age using projection*
```javascript
db.users.find({name: "User1"}, {_id:0, age:0})
```

output:
```javascript
[
  { name: 'User1', city: 'Mumbai' },
  { name: 'User1', city: 'Pune' }
]
```

4. findOne() :  Returns a single document object
```javascript
db.users.findOne({name: "User1"}, {_id:0, age:0})
```

*This returns the first document in the user's collection where the name field is "User1".*

output:
```javascript
[
  { name: 'User1', city: 'Mumbai' },
]
```
### *🔥Update Operations*
1. updateOne()
```javascript
 db.users.updateOne({ age: { $lt: 23 } }, { $set: { status: "active" } })
```

Output
```javascript
userdb> db.users.find({ age: { $lt: 23 } })
[
  {
    _id: ObjectId('65e23306dcee93f57058570f'),
    name: 'User1',
    age: 22,
    city: 'Mumbai',
    status: 'active'
  }
]
```

2. updateMany()
```javascript
db.users.updateMany({ age: { $gt: 23 } }, { $set: { status: "inactive" } })
```

Output
```javascript
userdb> db.users.find({ age: { $gt: 23 } })
[
  {
    _id: ObjectId('65e23306dcee93f570585710'),
    name: 'User1',
    age: 25,
    city: 'Pune',
    status: 'inactive'
  },
  {
    _id: ObjectId('65e23306dcee93f570585711'),
    name: 'User2',
    age: 30,
    city: 'Kalyan',
    status: 'inactive'
  }
]
```

### *🔥Delete Operations*
1. Delete Documents
- deleteOne()

```javascript
db.users.deleteOne({ name: "User2" })
```

Output
```javascript
userdb> db.users.find({},{_id:0})
[
  { name: 'User1', age: 22, city: 'Mumbai', status: 'active' },
  { name: 'User1', age: 25, city: 'Pune', status: 'inactive' }
]
```

- deleteMany()

```javascript
db.users.deleteMany({name:"User1"})
```

Output
```javascript
db.users.find()
Empty
```

2. Delete Collection
```javascript
db.users.drop()
```

Output
```javascript
userdb> show collections
posts
```

3. Delete Database

```javascript
db.dropDatabase()
```

Output
```javascript
{ ok: 1, dropped: 'userdb' }
```
