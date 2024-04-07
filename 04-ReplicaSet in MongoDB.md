# MongoDb Replication

> ###  Note: Make sure to create a folder for each node (primary and secondary)

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
