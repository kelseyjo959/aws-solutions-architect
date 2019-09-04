# Elastic Block Storage (EBS)

* **elastic block store or virtual hard disk**
* provides persistent block storage volumes for use with EC2
* each EBS is automatically replicated within its AZ for component failure protection
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
  * **Throughput Optimized Hard Disk Drive** - magnetic
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
    * for workloads that are accessed infrequently
    * **API name = Standard**
    * max IOPS.volume = 40-200

## Volumes & Snapshots

* `aws ec2 create-snapshot` to create EBS volume on CLI
* **Volumes exist on EBS**
* **Snapshots exist on S3**
* **Snapshots are points in time of Volumes**
* **Snapshots are ***incremental*** - only changed blocks are moved to S3**
* **For root Volume of EBS, stop EC2 Instance before taking a snapshot**
  * one can create a Snapshot while the instance is running but it might be a safer call to stop it

* AMI's can be created from both Volumes and Snapshots
* EBS Volume sizes can be changed on the fly, this includes size and storage type

* **Volumes will always be in the same AZ as the EC2 Instance**

* *Termination Protections is turned off by default*
* *When an EC2 Instance with EBS Root Volume is terminated, the root Volume is also terminated if specified on Console or CLI*
  * *however, any additional volumes on that Instance will continue to persist*

* **To move EC2 Volume from one AZ to another:**
  * Take a Snapshot
  * create AMI from Snapshot
  * use AMI to launch new EC2 Instance in a new AZ
    * This newly launched Instance can only be a limited amount of EC2 Types
* **To move EC2 Volume to another Region:**
  * Take a Snapshot
  * create AMI from Snapshot
  * Copy AMI from one Region to another
  * use copied AMI to launch new EC2 Instance into new Region

* Ephemeral EBS Volumes data will be deleted if the EBS-Backed EC2 Instance is stopped
* EC2s with Instance Store data will also be ephemeral if stopped

> *Back to EC2 Notes:* [**EC2 README**](./README.md)
