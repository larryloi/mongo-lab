
### Once MongoDB starts successfully:
```shell
docker exec -it mongo-1 mongosh -u root -p Abcd1234 --authenticationDatabase admin
```

```javascript
rs.initiate({
  _id: "rs0",
  members: [{ _id: 0, host: "mongo-1:27017" }]
})

rs.initiate({
  _id: "rs0",
  members: [
    { _id: 0, host: "mongo-1:27017" },
    { _id: 1, host: "mongo-2:27017" },
    { _id: 2, host: "mongo-3:27017" }
  ]
})

rs.initiate({
  _id: "rs0",
  members: [
    { _id: 0, host: "mongo-1:27017", priority: 1 },
    { _id: 1, host: "mongo-2:27017", priority: 0.5 },
    { _id: 2, host: "mongo-3:27017", priority: 0.5 }
  ]
})

rs.initiate({
  _id: "rs0",
  members: [
    { _id: 0, host: "db01.kaskade.local:21017" },
    { _id: 1, host: "db01.kaskade.local:22017" },
    { _id: 2, host: "db01.kaskade.local:23017" }
  ]
})
```

Then Kafka MongoDB Source Connector will be able to open change streams.


### Run the status command
Inside mongosh:
```javascript
rs.status()
```

### Show replica set configuration
```javascript
rs.conf()
```

### Show which node you’re connected to:
```javascript
db.isMaster()   // MongoDB ≤4.4
db.hello()      // MongoDB 5.0+
```

### List all members and their roles quickly:
```javascript
rs.status().members.map(m => `${m.name} - ${m.stateStr}`)
```