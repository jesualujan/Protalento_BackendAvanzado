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

MongoDB Enterprise >