# S3 Bucket

## READ THE AWS S3 BUCKET FAQs for Test Preparation

> [FAQ](https://aws.amazon.com/s3/faqs/)

## Introduction

* One of the oldest AWS Service offerings
* S3 stands for Simple Storage Service
* S3 provides developers and IT teams with secure, durable, highly scaleable object storage
* easy to use web interface to store and retrieve any amount of data from anywhere on the web
* safe place to store objects (flat files)
* stored data is spread across multiple devices and facilities

## Features

* **Object-based** storage (think files, only)
* **files can range from 0 Bytes to 5 TB**
* **unlimited storage**
* **files stored in Buckets** (think of a folder)
* **S3 s a universal name space**, names must be unique globally
  * Must be unique because a **unique web address** will be created
    * **HTTPS** link will consist of the aws region as well as the bucket name
* For file uploading, a **HTTP 200 code** will be received if upload successful
* *NOT* suitable for installing an operating system in a Bucket (use block based instead)

### Key Features

* **tiered storage available**
* **lifecycle management** - move to different tiers
* **versoining**
* **encryption**
* **multi factor authentication for DELETE**
* **secure data and control access with access control lists and bucket policies**

## Key Fundamentals of S3

* Objects are files
* **Key** : name of the object
* **Value** : sequence of bytes that makes up the data
* **Version ID** : allows for multiple versions of a file
* **Metadata** : data about the object being stored
* Subresources
  * **Access Control List** - permissions for object level or bucket level
  * **Torrent**

## S3 Data Consistency Model

* **read after write consistency** after PUTS of new objects - allows for immediate read of uploaded object
* **eventual consistency for overwrite** PUTS and DELETES - small amount of time must pass to propagate the update or delete

## S3 Guarantees

* 99.99% availability
* 99.999999999% durability of information (remember 11 9's)

> *Next Up:* [**S3 Tiers and Billing**](./tiers.md)

## Security and Encryption Basics

* newly created buckets are **private** by default
* buckets can be configured to create *access logs* that can then be sent to another bucket for log storage, or another bucket account
* **Access Control List**
* **Bucket Policies**

> *Next Up:* [**Security and Encryption**](./security-encryption.md)

## Version Control

* stores all versions of an object
  * this includes all writes and deletes
* great backup tool
* once versioning is enabled, it **cannot be disabled**
  * versioning can be suspended
* integrates with **Lifecycle Rules**
* Versioning's **MFA Delete** capability can add additional layer of security
* To un-do a object deletion, delete the 'delete marker' version
  * this will restore the object from the latest version before the delete marker

## Lifecycle Management and Glacier

* create lifecycle rules to manage objects
  * **use rules to automate transitions to tiered storage**
  * use rules to **expire** objects
  * can be used in conjunction with versioning
  * **apply rules to current or past versions**
  * transitions usually counted in days
  * configure expiration rules for permanent deletion
  * expiration rules for incomplete multi-part uploads

## Cross Region Replication

* **requires version control to be enabled on source and desintation**
* **regions must be unique**
* replicate entire bucket or by specific tags for object(s)
* chose buckets in same account or a different account
  * can also create new bucket at time of rule creation
* can change the storage tier at time of rule creation
* create or chose IAM role while setting up rule
* automatically gets same permissions as main bucket
* **existing objects are not replicated automatically**
  * **subsequent files will automatically replicated**
* **deleting individual versions or delete markers will not be replicated**

## Transfer Acceleration

* **uses the CloudFront Edge Network to accelerate uploads to S3**
  * can use a distinct url to upload to edge location which will then upload to S3
  * by uploading to Edge Network, the transfer can take place over **AWS backbone**
  * AWs built their own tool to test this acceleration

> *Next Up:* [**CloudFront**](./cloudfront.md)
> *Next Up:* [**Snowball**](./snowball.md)
> *Next Up:* [**Storage Gateways**](./storage-gateway.md)
