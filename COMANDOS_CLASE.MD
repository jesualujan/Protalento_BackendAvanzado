1) INICIAR LA BASE DE DATOS 
   EJECUTAR CMD EN MODO ADMINISTRADOR ESCRIBIR: mongod

2) INICIAR LA BASE DE DATOS 
   EJECUTAR CMD EN MODO ADMINISTRADOR ESCRIBIR: mongo
   esto es como el shell de mongo y podremos conectar nuestra base de datos

3) PODEMOS LIMPIAR LA CONSOLA CON CLS, NOSOTROS VAMOS A TRABAJAR EN LA SHELL DE       MONGO


4) MongoDB Enterprise > X=200
200
MongoDB Enterprise > X
200
MongoDB Enterprise > X/5
40
MongoDB Enterprise > X*2
400
MongoDB Enterprise > Math.sin(Math.PI/2)
1
MongoDB Enterprise > new Date()
ISODate("2023-08-17T20:22:52.777Z")
MongoDB Enterprise > new Date("2019/1/1")
ISODate("2019-01-01T06:00:00Z")
MongoDB Enterprise >

MongoDB Enterprise > function factorial(n) { if(n<=1) return 1; return n * factorial (n-1)}
MongoDB Enterprise > factorial
function factorial(n) { if(n<=1) return 1; return n * factorial (n-1)}
MongoDB Enterprise > factorial(5)
120
MongoDB Enterprise >

esto lo podemos hacer xk la shell de mongo es un interprete de javascript, y es como si escribieramos js puro =)

MongoDB Enterprise > db
test

para ver la base de datos actual que estamos usando escribimos db y nos muesta test por defecto


MongoDB Enterprise > show dbs
admin   0.000GB
config  0.000GB
local   0.000GB

MongoDB Enterprise > db
test
MongoDB Enterprise > help
        db.help()                    help on db methods
        db.mycoll.help()             help on collection methods
        sh.help()                    sharding helpers
        rs.help()                    replica set helpers
        help admin                   administrative help
        help connect                 connecting to a db help
        help keys                    key shortcuts
        help misc                    misc things to know
        help mr                      mapreduce

        show dbs                     show database names
        show collections             show collections in current database
        show users                   show users in current database
        show profile                 show most recent system.profile entries with time >= 1ms
        show logs                    show the accessible logger names
        show log [name]              prints out the last segment of log in memory, 'global' is default
        use <db_name>                set current database
        db.foo.find()                list objects in collection foo
        db.foo.find( { a : 1 } )     list objects in foo where a == 1
        it                           result of the last line evaluated; use to further iterate
        DBQuery.shellBatchSize = x   set default number of items to display on shell
        exit                         quit the mongo shell
MongoDB Enterprise > db.help()
DB methods:
        db.adminCommand(nameOrDocument) - switches to 'admin' db, and runs command [just calls db.runCommand(...)]
        db.aggregate([pipeline], {options}) - performs a collectionless aggregation on this database; returns a cursor
        db.auth(username, password)
        db.cloneDatabase(fromhost) - will only function with MongoDB 4.0 and below
        db.commandHelp(name) returns the help for the command
        db.copyDatabase(fromdb, todb, fromhost) - will only function with MongoDB 4.0 and below
        db.createCollection(name, {size: ..., capped: ..., max: ...})
        db.createUser(userDocument)
        db.createView(name, viewOn, [{$operator: {...}}, ...], {viewOptions})
        db.currentOp() displays currently executing operations in the db
        db.dropDatabase(writeConcern)
        db.dropUser(username)
        db.eval() - deprecated
        db.fsyncLock() flush data to disk and lock server for backups
        db.fsyncUnlock() unlocks server following a db.fsyncLock()
        db.getCollection(cname) same as db['cname'] or db.cname
        db.getCollectionInfos([filter]) - returns a list that contains the names and options of the db's collections
        db.getCollectionNames()
        db.getLastError() - just returns the err msg string
        db.getLastErrorObj() - return full status object
        db.getLogComponents()
        db.getMongo() get the server connection object
        db.getMongo().setSecondaryOk() allow queries on a replication secondary server
        db.getName()
        db.getProfilingLevel() - deprecated
        db.getProfilingStatus() - returns if profiling is on and slow threshold
        db.getReplicationInfo()
        db.getSiblingDB(name) get the db at the same server as this one
        db.getWriteConcern() - returns the write concern used for any operations on this db, inherited from server object if set
        db.hostInfo() get details about the server's host
        db.isMaster() check replica primary status
        db.hello() check replica primary status
        db.killOp(opid) kills the current operation in the db
        db.listCommands() lists all the db commands
        db.loadServerScripts() loads all the scripts in db.system.js
        db.logout()
        db.printCollectionStats()
        db.printReplicationInfo()
        db.printShardingStatus()
        db.printSecondaryReplicationInfo()
        db.resetError()
        db.runCommand(cmdObj) run a database command.  if cmdObj is a string, turns it into {cmdObj: 1}
        db.serverStatus()
        db.setLogLevel(level,<component>)
        db.setProfilingLevel(level,slowms) 0=off 1=slow 2=all
        db.setVerboseShell(flag) display extra information in shell output
        db.setWriteConcern(<write concern doc>) - sets the write concern for writes to the db
        db.shutdownServer()
        db.stats()
        db.unsetWriteConcern(<write concern doc>) - unsets the write concern for writes to the db
        db.version() current version of the server
        db.watch() - opens a change stream cursor for a database to report on all  changes to its non-system collections.


comandos: show dbs, db

para crear una nueva base datos usamos: use webstore

MongoDB Enterprise > use webstore
switched to db webstore
MongoDB Enterprise > db
webstore

MongoDB Enterprise > show dbs
admin   0.000GB
config  0.000GB
local   0.000GB

pero no nos muestra nuesta base de datos, puesto que necesitamos insertar algún dato entonces, creamos una colección para un producto =)

MongoDB Enterprise > db.products.insert({"name_product": "laptop"})
WriteResult({ "nInserted" : 1 })

MongoDB Enterprise > show dbs
admin     0.000GB
config    0.000GB
local     0.000GB
webstore  0.000GB

MongoDB Enterprise > show collections
products

MongoDB Enterprise > db
webstore

MongoDB Enterprise > db.dropDatabase()
{ "dropped" : "webstore", "ok" : 1 }

MongoDB Enterprise > show dbs
admin   0.000GB
config  0.000GB
local   0.000GB


MongoDB Enterprise > use webstore
switched to db webstore
MongoDB Enterprise > show collections
MongoDB Enterprise > db.createCollection("users")
{ "ok" : 1 }
MongoDB Enterprise > db
webstore
MongoDB Enterprise > show collections
users
MongoDB Enterprise > db.createCollection("products")
{ "ok" : 1 }
MongoDB Enterprise > db.createCollection("sellers")
{ "ok" : 1 }
MongoDB Enterprise > show collections
products
sellers
users
MongoDB Enterprise > db.help()
DB methods:
        db.adminCommand(nameOrDocument) - switches to 'admin' db, and runs command [just calls db.runCommand(...)]
        db.aggregate([pipeline], {options}) - performs a collectionless aggregation on this database; returns a cursor
        db.auth(username, password)
        db.cloneDatabase(fromhost) - will only function with MongoDB 4.0 and below
        db.commandHelp(name) returns the help for the command
        db.copyDatabase(fromdb, todb, fromhost) - will only function with MongoDB 4.0 and below
        db.createCollection(name, {size: ..., capped: ..., max: ...})
        db.createUser(userDocument)
        db.createView(name, viewOn, [{$operator: {...}}, ...], {viewOptions})
        db.currentOp() displays currently executing operations in the db
        db.dropDatabase(writeConcern)
        db.dropUser(username)
        db.eval() - deprecated
        db.fsyncLock() flush data to disk and lock server for backups
        db.fsyncUnlock() unlocks server following a db.fsyncLock()
        db.getCollection(cname) same as db['cname'] or db.cname
        db.getCollectionInfos([filter]) - returns a list that contains the names and options of the db's collections
        db.getCollectionNames()
        db.getLastError() - just returns the err msg string
        db.getLastErrorObj() - return full status object
        db.getLogComponents()
        db.getMongo() get the server connection object
        db.getMongo().setSecondaryOk() allow queries on a replication secondary server
        db.getName()
        db.getProfilingLevel() - deprecated
        db.getProfilingStatus() - returns if profiling is on and slow threshold
        db.getReplicationInfo()
        db.getSiblingDB(name) get the db at the same server as this one
        db.getWriteConcern() - returns the write concern used for any operations on this db, inherited from server object if set
        db.hostInfo() get details about the server's host
        db.isMaster() check replica primary status
        db.hello() check replica primary status
        db.killOp(opid) kills the current operation in the db
        db.listCommands() lists all the db commands
        db.loadServerScripts() loads all the scripts in db.system.js
        db.logout()
        db.printCollectionStats()
        db.printReplicationInfo()
        db.printShardingStatus()
        db.printSecondaryReplicationInfo()
        db.resetError()
        db.runCommand(cmdObj) run a database command.  if cmdObj is a string, turns it into {cmdObj: 1}
        db.serverStatus()
        db.setLogLevel(level,<component>)
        db.setProfilingLevel(level,slowms) 0=off 1=slow 2=all
        db.setVerboseShell(flag) display extra information in shell output
        db.setWriteConcern(<write concern doc>) - sets the write concern for writes to the db
        db.shutdownServer()
        db.stats()
        db.unsetWriteConcern(<write concern doc>) - unsets the write concern for writes to the db
        db.version() current version of the server
        db.watch() - opens a change stream cursor for a database to report on all  changes to its non-system collections.


ELIMINAR COLECCIONES:
MongoDB Enterprise > db.products.drop()
true
MongoDB Enterprise > show collections
sellers
users
MongoDB Enterprise > db.sellers.drop()
true
MongoDB Enterprise > db.users.drop()
true
MongoDB Enterprise > show collections
MongoDB Enterprise >


MongoDB Enterprise > show collections
MongoDB Enterprise > db.createCollections("products")
2023-08-17T15:32:20.887-0600 E  QUERY    [js] uncaught exception: TypeError: db.createCollections is not a function :
@(shell):1:1
MongoDB Enterprise > db.createCollection("products")
{ "ok" : 1 }
MongoDB Enterprise > show collections
products
MongoDB Enterprise > db.products.insert({
...     "name_product": "Huawei",
...     "price": 100,
...     "active": false,
...     "created_at": new Date("12/12/1999"),
...     "somedata": [1,"a",[]],
...     "facturer": {
...         "name": "P60 PRO",
...         "version": "Aqua",
...         "location": {
...             "city": "China",
...             "address": "ChinaTown"
...         }
...     }
... })
WriteResult({ "nInserted" : 1 })

MongoDB Enterprise > db.products.find()
{ "_id" : ObjectId("64de9211de1e2faf1d1c58ff"), "name_product" : "Huawei", "price" : 100, "active" : false, "created_at" : ISODate("1999-12-12T06:00:00Z"), "somedata" : [ 1, "a", [ ] ], "facturer" : { "name" : "P60 PRO", "version" : "Aqua", "location" : { "city" : "China", "address" : "ChinaTown" } } }
MongoDB Enterprise > db.products.find().pretty()
{
        "_id" : ObjectId("64de9211de1e2faf1d1c58ff"),
        "name_product" : "Huawei",
        "price" : 100,
        "active" : false,
        "created_at" : ISODate("1999-12-12T06:00:00Z"),
        "somedata" : [
                1,
                "a",
                [ ]
        ],
        "facturer" : {
                "name" : "P60 PRO",
                "version" : "Aqua",
                "location" : {
                        "city" : "China",
                        "address" : "ChinaTown"
                }
        }
}


MongoDB Enterprise > use mystore
switched to db mystore
MongoDB Enterprise > db
mystore
MongoDB Enterprise > db.createCollection("productos")
{ "ok" : 1 }
MongoDB Enterprise > show collections
productos
MongoDB Enterprise > db.products.insert({"name": "keyboard"})
WriteResult({ "nInserted" : 1 })
MongoDB Enterprise > db.products.find()
{ "_id" : ObjectId("64de92fade1e2faf1d1c5900"), "name" : "keyboard" }
MongoDB Enterprise > db.products.find().pretty()
{ "_id" : ObjectId("64de92fade1e2faf1d1c5900"), "name" : "keyboard" }
MongoDB Enterprise > db.products.insert({"name": "laptop", "price": 999.99})
WriteResult({ "nInserted" : 1 })
MongoDB Enterprise > db.products.find()
{ "_id" : ObjectId("64de92fade1e2faf1d1c5900"), "name" : "keyboard" }
{ "_id" : ObjectId("64de9338de1e2faf1d1c5901"), "name" : "laptop", "price" : 999.99 }
MongoDB Enterprise > db.products.insert([
...     {
...         "name": "mouse",
...         "description": "razer mouse",
...         "tags": ["computer", "gaming"],
...         "quantity": 14,
...         "created_at": new Date()
...
...     },
...     {
...         "name": "monitor",
...         "description": "benq",
...         "tags": ["computer", "gaming"],
...         "quantity": 5,
...         "created_at": new Date()
...     }
... ])
BulkWriteResult({
        "writeErrors" : [ ],
        "writeConcernErrors" : [ ],
        "nInserted" : 2,
        "nUpserted" : 0,
        "nMatched" : 0,
        "nModified" : 0,
        "nRemoved" : 0,
        "upserted" : [ ]
})

MongoDB Enterprise > db.products.find()
{ "_id" : ObjectId("64de92fade1e2faf1d1c5900"), "name" : "keyboard" }
{ "_id" : ObjectId("64de9338de1e2faf1d1c5901"), "name" : "laptop", "price" : 999.99 }
{ "_id" : ObjectId("64de943bde1e2faf1d1c5902"), "name" : "mouse", "description" : "razer mouse", "tags" : [ "computer", "gaming" ], "quantity" : 14, "created_at" : ISODate("2023-08-17T21:42:19.902Z") }
{ "_id" : ObjectId("64de943bde1e2faf1d1c5903"), "name" : "monitor", "description" : "benq", "tags" : [ "computer", "gaming" ], "quantity" : 5, "created_at" : ISODate("2023-08-17T21:42:19.902Z") }

MongoDB Enterprise > db.products.find().pretty()
{ "_id" : ObjectId("64de92fade1e2faf1d1c5900"), "name" : "keyboard" }
{
        "_id" : ObjectId("64de9338de1e2faf1d1c5901"),
        "name" : "laptop",
        "price" : 999.99
}
{
        "_id" : ObjectId("64de943bde1e2faf1d1c5902"),
        "name" : "mouse",
        "description" : "razer mouse",
        "tags" : [
                "computer",
                "gaming"
        ],
        "quantity" : 14,
        "created_at" : ISODate("2023-08-17T21:42:19.902Z")
}
{
        "_id" : ObjectId("64de943bde1e2faf1d1c5903"),
        "name" : "monitor",
        "description" : "benq",
        "tags" : [
                "computer",
                "gaming"
        ],
        "quantity" : 5,
        "created_at" : ISODate("2023-08-17T21:42:19.902Z")
}
MongoDB Enterprise > db.products.find({
...
... name:"mouse"})
{ "_id" : ObjectId("64de943bde1e2faf1d1c5902"), "name" : "mouse", "description" : "razer mouse", "tags" : [ "computer", "gaming" ], "quantity" : 14, "created_at" : ISODate("2023-08-17T21:42:19.902Z") }
MongoDB Enterprise >