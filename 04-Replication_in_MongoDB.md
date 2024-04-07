# MongoDb Replication

<img align="center" width="480"  src='./replication.png'/>

> ###  Note: Make sure to create a folder for each node (primary and secondary)
<img align="center" width="250"  src='./replsetfolder.png'/>

## Configure Primary Node (Port 27017)
```javascript
mongod --port 27017 --dbpath C:\Replication\primary --replSet rs
```
## Configure Secondary Node 1 (Port 27018)
```javascript
mongod --port 27018 --dbpath C:\Replication\replicaset1 --replSet rs
```
## Configure Secondary Node 2 (Port 27019)
```javascript
mongod --port 27019 --dbpath C:\Replication\replicaset2 --replSet rs
```
## Connect to MongoDB Shell (Port 27017)
```javascript
mongosh --port 27017
```
## Initialize the Replication Set
```javascript
rs.initiate({_id: "rs", members: [{_id: 0, host: "localhost:27017"}, {_id: 1, host: "localhost:27018"}, {_id: 2, host: "localhost:27019"}]})
```
## Check Replication Set Status
```javascript
rs.status()
```
Output:
```javascript
  members: [
    {
      _id: 0,
      name: 'localhost:27017',
      health: 1,
      state: 1,
      stateStr: 'PRIMARY',
      uptime: 36,
      syncSourceHost: '',
      syncSourceId: -1,
    },
    {
      _id: 1,
      name: 'localhost:27018',
      health: 1,
      state: 2,
      stateStr: 'SECONDARY',
      uptime: 19,
      syncSourceHost: 'localhost:27017',
      syncSourceId: 0,
    },
    {
      _id: 2,
      name: 'localhost:27019',
      health: 1,
      state: 2,
      stateStr: 'SECONDARY',
      uptime: 12,
      syncSourceHost: 'localhost:27018',
      syncSourceId: 1,
    }
  ]
```

## Create a Database and Collection in the Primary Node
```javascript
use testdb
```
```javascript
db.testcollection.insertOne({name: "example"})
```

## Check if Database and Collection Exist in Secondary Nodes
### > Connect to Secondary Node 1 (Port 27018)
```javascript
mongosh --port 27018
```
## Check if the database exists
```javascript
use testdb
```
```javascript
db.testcollection.find()
```
