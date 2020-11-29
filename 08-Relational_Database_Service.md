## Database Refresher - part 1

#

- DBs store and manage data
- there are diff types of systems
- relational (SQL) vs non-relational(NoSQL)

- relational dbs: (RDBMS)
  - structured. uses Schema
  - relationship between tables
- NoSQl:

  - not one single thing. everything that isnt RDBMS
  - much more relaxed
  - relationships are handled diff

- relational ex
  - ![ex rdbms](img/rdsexample.png '2 tables with composite table')

## Database Refresher - part 2

#

- types of NoSQL dbs:
  1. key value - what I think it is. Scalable. used for in memory caching
  2. wide column store - variation of key/value. ex: dynamoDB
  - ![wide col store](img/rdswidecolstore.png 'ex of wide col store')
  3. document - store/query data as documents. JSON or XML. order db, collections, deep attributes
  - ![ex of doc db](img/rdsdocdb.png 'ex of a doc db')
  4. column databases - diff than row dbs(sql). solve limitations of row dbs. row dbs - (OLTPS). column dbs store data in columns. good for reporting. aws ex is Redshift
  - ![ex of col db](img/rdscoldbs.png 'ex of a col db vs a row db')
  5. graphs - think graphQL. uses nodes and edges. relationships are also stored in db. makes them fast
  - ![rds graph ex](img/rdsgraphdb.png)

## Databases on EC2

#

## Relational Database Services (RDS) Architecture

#

## RDS High-Availability (Multi AZ)

#

## RDS Automatic Backup, RDS Snapshots and Restore

#

## RDS Read-Replicas

#

## Aurora Architecture

#

## Aurora Global Database

#

## Mulit-master writes

#

## Database Migration Service (DMS)

#
