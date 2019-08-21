# EBS

* **elastic block store or virtual hard disk**
* provides persistent block storage volumes for use with EC2
* each EBS is automatically replicated within its Availability Zone for component failure protection
* *5 Types*
  * **General Purpose SSD**
    * balance price and performance
    * for most work loads
    * **API name = gp2**
    * max IOPS.volume = 16,000
  * **Provisioned IOPS SSD**
    * highest performance
    * for databases
    * **API name = io1**
    * max IOPS.volume = 64,000
  * **Throughput Optimised Hard Disk Drive** - magnetic
    * low cost HHD for frequently accessed, throughput intensive workloads
    * for big data and data warehouses
    * **API name = st1**
    * max IOPS.volume = 500
  * **Cold Hard Disk Drive** - magnetic
    * lowest cost HHD for less frequently accessed
    * for file servers
    * **API name = sc1**
    * max IOPS.volume = 250
  * **EBS Magnetic**
    * previous generation HHD
    * for workloads that are accessed infreqently
    * **API name = Standard**
    * max IOPS.volume = 40-200

## Volumes & Snapshots

* **Volumes exist on EBS**
* **Snapshots exist on S3**
* **Snapshots are points in time of Volumes**
* **Snapshots are incremental - only changed blocks are moved to S3**
* **For root Volume of EBS, stop EC2 Instance before taking a snapshot**
  * one can create a Snapshot while the instance is running but it might be a safer call to stop it

* AMI's can be created from both Volumes and Snapshots
* EBS Volume sizes can be changed on the fly, this includes size and storage type

* **Volumes will always be in the same AZ as the EC2 Instance**

* When an EC2 Instance with Volume is terminated, the root Volume is also terminated
  * however, any additional volumes on that Instance will continue to persist

* **To move EC2 Volume from one AZ to another:**
  * Take a Snapshot
  * create AMI from Snapshot
  * use AMI to launch new EC2 Instance in a new AZ
    * This newly launched Instance can only be a limited amount of EC2 Types
* **To move EC2 Volum to another Region:**
  * Take a Snapshot
  * create AMI from Snapshot
  * Copy AMI from one Region to another
  * use copied AMI to launch new EC2 Instance into new Region

> *Back to EC2 Notes:* [EC2 README](./README.md)
