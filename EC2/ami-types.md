# AMI Types

## EBS vs Instance Store

* select AMI Type based on following criteria under Community AMIs:
  * Region
  * Operating System
  * Architecture (32 bit or 64 bit)
  * Launch Permissions
  * Storage for Root Device (Root Device Volume)
    * both ROOT Volumes will be deleted upon termination
    * **Instane Store** - *ephemeral storage*
      * root device for instance launched from the AMI is an instance store volume created from a template stored in AWS S3
      * *cannot be stopped*
      * *if underlying host fails, data will be lost*
      * reboot will not lose data
    * **EBS Backed Volumes**
      * root device for an instance launched from the AMI is an AWS EBS Volume created from AWS EBS Snapshot
      * *can be stopped*
      * reboot will not lose data
      * upon termination, can tell AWS to keep an EBS Root Volume upon termination of Instance

> *Back to EC2 Notes:* [EC2 README](./README.md)
