# MongoDB Operators

MongoDB operators are special keywords used in queries and updates to perform specific operations on data. These operators enhance the flexibility and power of MongoDB queries and updates.


## Comparison Operators

Comparison operators are used to compare values in a query. Some common comparison operators include:
- `$eq`: Matches values that are equal to a specified value.
- `$gt`: Matches values that are greater than a specified value.
- `$lt`: Matches values that are less than a specified value.
- `$gte`: Matches values that are greater than or equal to a specified value.
- `$lte`: Matches values that are less than or equal to a specified value.
- `$ne`: Matches all values that are not equal to a specified value.
- `$in` : Matches any of the values specified in an array.

*Dataset Name:* `bank.sales.csv` [Click to Download Dataset](https://github.com/AsadCodeCraft/MongoDB/blob/main/bank.sales.csv)
### Find one document where Value is greater than 100000
```javascript
db.sales.findOne({ Value: { $gt: 100000 } })
```

### Find Number of documents where Transaction_count is less than or equal to 1000
```javascript
db.sales.find({ Transaction_count: { $lte: 1000 } }).count()
```

### Find Number of documents where Location is an array containing 'Mumbai'
```javascript
db.sales.find({ Location: { $in: ['Mumbai' , 'Pune'] } }).count()
```
## Logical Operators

Logical operators are used to perform logical operations in a query. Some common logical operators include:
- `$and`: Joins query clauses with a logical AND and returns all documents that match the conditions of both clauses.
- `$or`: Joins query clauses with a logical OR and returns all documents that match the conditions of either clause.
- `$not`: Inverts the effect of a query expression and returns documents that do not match the query expression.
- `$nor`: Joins query clauses with a logical NOR and returns all documents that fail to match both clauses.

### Find documents where Location is 'Mumbai' or 'Delhi' using logical operators
```javascript
db.sales.find({ $or: [ { Location: 'Mumbai' }, { Location: 'Delhi' } ] })
```

### Find documents where Domain is 'RETAIL' and Location is 'Pune' using logical operators
```javascript
db.sales.find({ $and: [ { Domain: 'RETAIL' }, { Location: 'Pune' } ] })
```

## Element Operators

Element operators are used to check for the existence of fields or values within documents. Some common element operators include:
- `$exists`: Matches documents that contain the specified field.
- `$type`: Matches documents based on the BSON type of the field.

### Find documents where Transaction_count does not exist
```javascript
db.sales.find({ Transaction_count: { $exists: false } })
```

### Find documents where the 'Value' field is of type number (double)
```javascript
db.sales.find({ Value: { $type: 'double' } })
```
    
### Find Number of documents where Domain exists
```javascript
db.sales.find({ Domain: { $exists: true } }).count()
```

## Array Operators

Array operators are used to query arrays within documents. Some common array operators include:
- `$elemMatch`: Matches documents that contain an array field with at least one element that matches all the specified query criteria.
- `$size`: Matches documents where the array field is a specific size.
