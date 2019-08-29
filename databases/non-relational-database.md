# Non Relational Databases

## AWS DynamoDB

* AWS's NoSQL Service
* best for apps that need consistent, single-digit millisecond latency at any scale
* supports both document and key-value data models
* flexible data model and reliable performance make it great for mobile, web gaming, ad-tech, IoT

* **data is stored on SSD Storage**
* **spread across 3 distinct geographic data centers** (redundancy)
* **eventual consistent reads (default setting)**
  * consistency across all data is reached within one second
  * *if an update is made, a 1 second delay occurs so if immediate read is needed, do not use this option*
* **strongly consistent reads**
  * returns a result that reflects all writes that received a successful response prior to the read
  * *best for apps that need an update within less than a second upon an update*
* DynamoDB Headers attributes:
  * x-amz-date
  * x-amz-target
  * host
  * content-type

## Redshift

* **business intelligence**
* fast, powerful, fully managed, petabyte scale, data warehouse service
* Different Configurations:
  * Single Node (160Gb)
  * Multi-Node
    * Leader Node (manages client connections and receives queries)
    * Compute Node (store data and perform queries and computations)
      * up to 128 Compute Nodes
* Redshift uses Advanced Compression
  * individual columns are compressed rather than row based
  * does not require indexes or materialized views which uses less space than traditional Relational DB systems
  * AWS Redshift automatically samples data and selects most appropriate compressions scheme

* Massively Parallel Processing (MPP)
  * automatically distribute data query load across all nodes
  * easy to add nodes to data warehouse
  * enables maintaining fast query performance as data warehouse grows

* Backups are enabled by default
  * **default is 1 day retention period**
  * **maximum retention is 35 days**
  * **Redshift will attempt to keep at least 3 bakcups**
  * Redshift will **asynchronously replicate snapshots** to S3 in another Region for disaster recovery

* Redshift Pricing
  * based on Compute Node Hours
    * total number of hours run across all the Compute Nodes for a billing period
    * billed for 1 unit node per hour
    * will not be charged for Leader Node Hours, only Compute Node Hours
  * charged for Backups
  * charged for Data Transfers (only within VPC, not outside)

* Security Considerations
  * encrypted in transit using SSL
  * encrypted at rest using AES-256 encryption
  * by default Redshift takes care of key management
    * can manage your own through
      * HSM (Hardware Security Module)
      * AWS Key Management Service

* Redshift Availability
  * **currently only available in 1 AZ**
  * can restore snapshots to new AZ in the event of outage

> *Back to Database Notes:* [Databases README](./README.md)
