# Relational Database Services

## RDS Basic Info

* **RDS runs on Virtual Machines**
* **These virtual machines cannot be accessed**
* **RDS is not serverless** exception = Aurora
* upon RDS Instance creation, AZ can be chosen

* RDS 2 key features:
  * Multi-AZ for diaster recovery
    * think hot swappable with no need to change url
  * Read Replicas for performance
    * secondary db gets replicated data but a failure would need a url change
    * up to 5 copies at once
    * good for re-directing huge loads of requests

## RDS Backups

* **upon restoration, either type will create a new Instance with a new DNS endpoint**
* 2 different types of RDS Backups:
  * Automated Backups
    * recover database at any point in time within a 'retention period'
      * retention period = 1 -35 days
    * automated backups take a daily snapshot as well as store transaction logs
      * upon recovery, most recent backup is chosen
      * applicable transaction logs will be applied
      * this process allows restoration up to the second within the retention period
    * **enabled by default**
    * backups stored in S3 with equal size of storage compared to your database
    * backups taken during time window
      * *during that window, elevated latency could occur due to the increased I/O*
  * Database Snapshots
    * **manual process**
    * snapshots are stored even if the RDS Instance is deleted, unlike Automated Backups

## Encryption At Rest

* **supported by MySQL, Oracle, SQL Server, PostgreSQL, MariaDB & Aurora**
* **encryption done with AWS KMS**
* **encryption includes the data, its automated backups, read replicas, and snapshots**

## Multi-AZ

* copies data to other AZs **synchronously** by AWS
  * if an AZ fails, AWS updates the IP addresses and no administrative intervention is needed
* **can force a fail-over from one AZ to another by rebooting RDS Instance**
* good for production environments
* **for disaster recovery only**
* **available for these services:**
  * SQL Server
  * Oracle
  * MySQL Server
  * PostgreSQL
  * MariaDB
* Available for RDS Reserved Instances

## Read Replicas

* **used to increase performance**
* **can be Aurora or MySQL**
* production database **asynchronously** replicates to multiple copies
* can have read replica inceptions (read replica reads another replica)
* **allows for a read-only replica of the database**
* **must have Automatic Backups enabled**
* can have up to 5 read replica copies of a database
* can have read replicas of read replicas but beware of latency
* used for scaling, not for DR
* unique DNS endpoint for each instance
* **can be multiple AZs**
* *can be promoted to be the leader but this will break the replication process**
* a Read Replica can be in a different Region

> *Back to Database Notes:* [Databases README](./README.md)
