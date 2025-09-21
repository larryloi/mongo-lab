
### Once MongoDB starts successfully:
```shell
docker exec -it mongo mongosh -u root -p Abcd1234 --authenticationDatabase admin
```

```javascript
rs.initiate({
  _id: "rs0",
  members: [{ _id: 0, host: "mongo:27017" }]
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