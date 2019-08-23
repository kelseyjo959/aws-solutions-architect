# AWS DATABASES

## Basic Database Info

### Relational Databases

* relational database is like a spreadsheet
  * different sheets are like tables
    * rows within those tables
      * fields or columns within row
* **6 AWS Relational Databases**
  * SQL Server
  * Oracle
  * MySQL Server
  * PostgreSQL
  * Aurora
  * MariaDB
* **Relational Database Services** (RDS) 2 key features
  * Multi-AZ for diaster recovery
    * think hot swappable with no need to change url
  * Read Replicas for performance
    * secondary db gets replicated data but a failure would need a url change
    * up to 5 copies at once
    * good for re-directing huge loads of requests
* **RDS runs on virtual machines but there is no access to these machines**
* **RDS is not serverless** exception = Aurora

### Non Relational Databases

* Collection = Table
  * Document = Row
    * Key Value Pairs = Fields
* **AWS DynamoDB**

### Data Warehousing

* used for business intelligence
* used to pull in large and complex data sets ususally by management
* *Online Transaction Processing (OLTP) in RDS*
  * more simple query to find data
* Online Analytics Processing (OLAP)
  * pulls in large amounts of data and does a lot of queries
* AWS Data Warehouse Solution for OLAP = **Redshift**

### ElastiCache

* ElastiCache is a web service that can deploy, operate, and scale in-memory cache in the cloud
  * improves performance of existing databases for web apps by reducing access times
  * frequent identical queries
  * supports 2 open source in-memory caching engines:
    * MemcacheD
    * Redis

