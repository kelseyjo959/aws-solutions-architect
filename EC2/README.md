# Elastic Compute Cloud (EC2)

## Introduction

* provides sizeable compute capacity in the cloud
* reduces time required to obtain and boot new server instances to minutes
* short spin up time allows for quick scale capacity, up or down

## Pricing Models

* pay for what is used, as you go
* pay less as it is used more
* pay even less when you reserve capacity
* **ON DEMAND**
  * users wanting low cost and flexibility without any up-front payment or long term commitment
  * best for apps that are short term, spiky, or unpredictable workloads that cannot be interupted
  * **fixed rate pricing by the hour, min, sec, etc with no commitment**
* **RESERVED**
  * best for apps with steady state or predictable use that require reserved capacity
  * users able to make upfront payments to reduce total computing costs
  * provides **capactity reservation**, offer discount on the hourly charge with **contract term 1 or 3 years**
  * Pricing Types
    * Standard Reserved Instances
      * offer up to 75% off on demand instances
      * **more paid up front, the more available savings**
    * Convertible Reserved Instances
      * offer up to 54% off on demand instances
      * allows switching between Instance types for equal or greater value
    * Scheduled Reserve Instances
      * available to launch within reserved time window
      * allows for matching usage capacity to predictable times (everyone logging in at the same time)
* **SPOT**
  * only feasible for apps that require only low compute prices
  * for users with urgent computing needs for large amounts of additional capacity
  * **price bidding** available for when there is extra capacity. When that capacity is lost, an instance can potentiall by shut down in a matter of minutes
  * **best for apps with flexible start and end times**
  * if Spot instance terminated by AWS, will not be charged for partial hour
    * if instance is terminated by user, will be charged for **any hour in which the instance ran**
* **DEDICATED HOSTS**
  * useful for regulatory requirements that may not support multi-tenant virtualization
  * good for licensing which does not support multi-tenancy or cloud  deployments
  * can be purchased on demand at an hourly rate
  * can be purchased as a Reservation for up to 70% off the On-Demand price
  * **physical EC2 server dedicated for use**
  * reduce costs by using existing server-bound software licenses

* EC2 Instance Types *not needed for test but useful info*
![EC2 Instance Types](../images/ec2-instance-types.png)
* EC2 Mnemonic- Fight Dr Mcpxz in Australia
![EC2 Mnemonic](../images/ec2-instances-mnemonic.png)

> *Next Up:* [**EC2 Lab Notes**](./ec2-lab-notes.md)

## Security Groups Basics

* **changes to Security Groups take effect immediately**
* Security Groups are **stateful** - a change to an inbound rule effects the outbound
* **cannot block a particular port or IP address within Security Groups**
  * **inbound traffic is blocked by default**
  * **all outbound traffic is allowed by default**
* **any number of EC2 instances for a Security Group**
* **multiple Security Groups can be attached to an EC2 Instance**

> *Next Up:* [EBS and Volumes](./ebs-and-volumes.md)
> *Next Up:* [AMI Types](./ami-types.md)
> *Next Up:* [EBS and Encryption](./encryption.md)
