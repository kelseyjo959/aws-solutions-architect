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

## Created Acronyms

* AZ = Availability Zone
