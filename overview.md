# Amazon Web Services

## Solutions Architect - Associates

### Introduction

The overview below covers the need to know in the High Level Services section below. The other sections, such as Compute, Databases and more, will be updated / covered in later notes as I progress with my studying.

### Services Overview

#### High Level Services

* AWS Global Infrastructure Terms
  * **Availability Zone** - Data center (may be several coupled together) engineered to be isolated from failures. Currently 57 Zones (2018)
  * **Region** - Two or more **Availability Zones** Represent separate geographic areas. Currently 19 Regions (2018)
        * US East (Northern Virginia) with 6 Availability Zones
        * US East (Ohio) with 3 Zones
        * US West (Oregon) with 3 Zones
        * US West (Northern California) with 3 Zones
        * GovCloud (US-West) with 3 Zones
        * GovCloud (US-East) with 3 Zones
        * Canada (Central) with 2 Zones
    * **Edge Locations** - Endpoints for AWS used for caching content (usually CloudFront). More Edge Locations than Regions
      * **CloudFront** - Is Amazon's Content Delivery Network (CDN).
* Need to know;
  * Analytics
  * _**Compute**_  (EC2 & Lambda)
  * _**Databases**_ (RDS, DynamoDB, Redshitft)
  * Desktop & App Streaming
  * Machine Learning
  * Management & Governance
  * Migration & Transfer
  * _**Network & Content Delivery**_ ( Route 53, VPCs)
  * _**Security, Identity & Compliance**_  (IAM)
    * [Identity Access Management](./identity-access-management/README.md)
  * _**Storage**_ (S3 Buckets)

    > **Note**: Bold and italic list items from above are the main ones to study.

## Acronyms

* AMI = Amazon Machine Images
* ALB = Application Load Balancer
* AZ = Availability Zone
* CDN = Content Delivery Network
* DNS = Domain Name Service
* EBS = Elastic Block Storage
* EC2 = Elastic Cloud Computing
* ECS = Elastic Container Service
* EFS = Elastic File System
* ELB = Elastic Load Balancer
* IA = Infrequently Accessed
* IAM = Identity Access Management
* MFA = Multi Factor Authentication
* NACL = Network Access Control List
* NAT = Network Address Translation
* NLB = Network Load Balancer
* OLTP = Online Transaction Processing (think RDS)
* OLAP = Online Analytics Processing (think Redshift)
* RDS = Relational Database Service
* S3 = Simple Storage Service
* SNS = Simple Notification Server
* SSE = Server Side Encrpytion
* SWF = Simple Work Flow
* TTL = Time To Live
* VPC = Virutal Private Cloud
* VTL = Virtual Tape Library
