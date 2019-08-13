# S3 Buckets

## Tiers

* S3 Standard
  * **99.99% availability**
  * **99.999999999% durability**
  * availability zones >= 3
  * minimum capacity charge per object = null
  * minimum storage duration charge = null
  * retrieval fee = null
  * first byte latency = milliseconds
    * redundant storage designed to sustain up to 2 concurrent facility losses

* S3 IA (Infrequently Accessed)
  * 99.9% availability
  * 99.999999999% durability
  * availability zones >= 3
  * minimum capacity charge per object = 128KB
  * minimum storage duration charge = 30 days
  * retrieval fee = per GB retrieved
  * first byte latency = milliseconds
    * data that will be accessed **less frequently**
    * **rapid access** still featured
    * lower fee than Standard but **retrieval fee** is charged

* S3 One Zone - IA (old name = RRS)
  * 99.5% availability
  * 99.999999999% durability
  * availability zones = 1
  * minimum capacity charge per object = 128KB
  * minimum storage duration charge = 30 days
  * retrieval fee = per GB retrieved
  * first byte latency = milliseconds
    * lower-cost option for infrequently accessed data
    * **does not support multiple Availability Zone data resilience**

* S3 Intelligent Tiering
  * 99.9% availability
  * 99.999999999% durability
  * minimum capacity charge per object = null
  * availability zones >= 3
  * minimum storage duration charge = 30 days
  * retrieval fee = null
  * first byte latency = milliseconds
    * **designed to optimize cost**
    * automatically moves data to most cost-effective access tier
    * no performance impact or operational overhead
    * uses **machine learning** to learn how often objects are used

* S3 Glacier
  * 99.999999999% durability
  * availability zones >= 3
  * minimum capacity charge per object = 40KB
  * minimum storage duration charge = 90 days
  * retrieval fee = per GB retrieved
  * first byte latency = select hours or minutes
    * secure, durable and low-cost storage for data archiving
    * **retrieval times vary from minutes to hours**
    * reliably store any amount of data at competitive costs cheaper than on-premise solutions

* S3 Glacier Deep Archive
  * 99.999999999% durability
  * availability zones >= 3
  * minimum capacity charge per object = 40KB
  * minimum storage duration charge = 180 days
  * retrieval fee = per GB retrieved
  * first byte latency = select hours
    * **lowest-cost storage tier**
    * **retrieval time of up to 12 hours**

## Billing

* charged for:
  * storage
  * requests
  * storage management
  * data transfer
  * transfer acceleration
    * enables fast and secure transfers of files over long distances between end users and bucket
    * uses AWS Cloudfront's globally distributed edge locations
      * upon arrival at edge location, data is routed to S3 over optimized network path
      * utilizes Amazon's Backbone Network
  * cross region replication
    * upon upload to one region, automatically replicated to another region

## READ THE AWS S3 BUCKET FAQs for Test Preparation

* [FAQ](https://aws.amazon.com/s3/faqs/)
