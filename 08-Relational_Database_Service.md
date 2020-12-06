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

- pros and cons of running DBMS systems directly on EC2

  - one approach is to have everything in one ec2(monolithic?)
  - another is to have architecture split amongst multiple AZs

    - cost considerations, connection considerations

      ![db architecture example](img/rdsec2archtypes.png '2 diff ex of arch type setup for ec2')

  - why you might run a db on ec2:

    - access to db instance OS
    - advanced db option tuning
    - using a DB aws doesnt support

      ![rds on ec2 pros](img/rdspros.png)

  - why you shouldnt:

    - admin overhead
    - backups and disaster recovery mgmt
    - EC2 runs on a single AZ. if that zone fails, db could fail
    - features. AWS db products have amazing features
    - EC2 is on/off - no serverless or easy scaling
    - replication
    - performance

      ![rds cons](img/rdscons.png "why you shouldn't")

    - next 2 lessons dedicated to demos. Migrating the wordpress db monolithic to a dedicated EC2 db

## Relational Database Services (RDS) Architecture

#

- lesson covers high level architecture of the product and details what engines are supported, access methods, and other key concepts
- described as database-as-a-service(DBaaS)
- provides managed database instance (can hold 1+ databases)
  - think of it acting as a ec2 db server
- multiple engines:
  1. mysql
  2. mariadb
     3.postgres
     4.oracle
  3. MS sqlserver
- supports Amazon Aurora - will be it's own lesson in the future

  - ![rds arch ex for lessons](img/rdsarchitecture.png)

- RDS instance
  - access it using a CNAME
  - can use existing tooling to access db
  - comes in diff sizes similar to ec2 instances
  - can be single AZ or multi AZ
  - you provision instance
    - comes w/block storage in same AZ
    - can fail because all in one AZ
- billing
  - billed for instance
  - also billed for storage
- security handled via security group

  - ![rds instance details](img/rdsinstances.png)

- next two lessons are demos
  1. migrating a mariadb into RDS part 1
  2. migrating a mariadb into RDS part 2

## RDS High-Availability (Multi AZ)

#

- feature that provisions a standby replica which is kept in sync Synchronously with the primary instance

  - cannot be used for performance scaling..only availability
  - backups, software updates, and restarts can take advantage of MultiAZ to reduce user disruption

- when it's enabled, secondary hardware is allocated inside a diff AZ
  - known as standby replica
- you only access RDS using the CNAME. it normally points to the primary instance
- uses synchronous replication
  - as soon as data is written to primary RDS drive, it is sent to secondary drive and written
  - very little if any lag
- if primary fails, database automatically points to secondary CNAME

  - happens quickly
  - is Highly Available but not fault tolerant

  - ![rds multiAZ architecture](img/rdsmulitaz.png)

exam power ups

1. multi AZ is not free tier. costs extra
2. standby replica cannot be accessed directly. no performance improvement, it's a failover improvement
3. failover takes 60 - 120 seconds
4. same region only other AZs in the same VPC
5. backups are taken from the Standby
6. az outages, primary failure, instance type change, software patching

## RDS Automatic Backup, RDS Snapshots and Restore

#

- RDS is capable of performing manual snapshots and autobackups

  - manual snapshots are perfomed manually and live past the termination of the RDS instance
  - Automatic backups can be taken of an RDS instance with a 0(disabled) to 35 day retention
    - Automatic backups also use S3 for storing transaction logs every 5 minutes - allowing for point in time recovery
  - snapshots can be restored, but create a new RDS instance

- important topic for exam and real world usage
- ** RTO and RPO ** two important objectives

1. RTO - recovery time objective

- time between failure and full restore of service

2. RPO - recovery point objective

- time between the last bkup and the failure
- represents max amt of data lost possible
- lower the rpo, higher the cost

  - ![rto vs rpo chart](img/rdsrtorpo.png)

- rds backups

  - automatic bkups vs manual bkups
  - manual bkups live forever
  - automatic have a retention rate of 0 - 35
  - can use transaction logs for 5 minute level of granularity

    ![rds backups](img/rdsbackups.png)

- exam power ups

  1. restores create a new RDS instance - new address
  2. restoring a manual snapshot restores single point in time

  - increases rpo

  3. auto bkups are diff because of transaction logs
  4. restores arent fast think about rto

  - ![rds restores exam powerup](img/rdsrestoresexampu.png)

## RDS Read-Replicas

#

- read replicas can be added to an RDS instance - 5 direct per primary instance

  - can be in the same region or cross region replicas
  - provide read performance scaling for the instance, but also offer low rto recovery for any instance failure issues
  - don't help w/data corruption as the corruption will be replicated to the RR

- RR provide two main benefits - performance and availability
  - read only replicas of an RDS instance
  - can use for read operations
  - own db endpt address
- kept in sync using Asynchronous replication
- data is written fully to the primary instance first, then written to secondary replica instance
  - in theory could lead to lag, depends on connection
- can be created in same region or diff region

  - if cross region , AWS handles config, it just works

  ![rds read replica architecture](img/rdsreadreplica.png)

- why do they matter?

  - read performance improvements

    - 5x direct read replicas per db instance
    - each provide additional instance of read performance
    - can have read replicas of read replicas, but lag can start to be a problem
    - global perform improvements

    - ![rds read replicas performance improvements](img/rdsreadperform.png)

  - availability improvements

    - snapshots and bkups improve RPO
    - rtos are still a problem
    - read replicas offer near zero RPO
    - read replicas can be promoted quickly to primary - low RTO - only works for failures
    - failure only. watch for data corruption. corruption gets replicated as well :(
    - read only until promoted. not reversable
    - global availability improvements - global resilience

    - ![rds read replicas availability improvements](img/rdsreadavailability.png)

  - next 2 lessons are Demos:
    - using a snapshot and restore to recover data from corruption part 1
    - using a snapshot and restore to recover data from corruption part 2

## Aurora Architecture

#

## Aurora Global Database

#

## Mulit-master writes

#

## Database Migration Service (DMS)

#
