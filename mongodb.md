# MongoDB

## Mongorestore

Only user with [restore role](https://docs.mongodb.com/manual/reference/built-in-roles/#backup-and-restoration-roles) on *admin* database can restore databases.

```
use admin
db.grantRolesToUser('admin', ['restore'])
```

## Get Users

```
use <db-name>   // use 'admin' for DB administrators
db.getUsers()
```


## Sort documents by field length

```
db.spots.aggregate([
  { $addFields: { length: { $strLenCP: '$fieldName' } } },
  { $sort: { fieldName: -1 }}
])
```