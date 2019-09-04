# CloudWatch

* Monitoring service for monitoring AWS resources as well as AWS applications
* create CloudWatch alarms that trigger notifications
* **Standard Monitoring = 5 mins**
* **Detailed Monitoring = 1 min**
* Performance Monitoring of:
  * Compute
    * EC2 Defaults:
      * CPU utilization
      * Disk performance
      * Network utilization
      * Disk Reads/Writes
    * Auto scaling groups
    * Elastic load balancers
    * Route53 health checks
  * Storage & Content Delivery
    * EBS Volumes
    * Storage Gateway
    * CloudFront

* Host Level Metrics Consist of:
  * CPU
  * Network
  * Disk
  * Status Check

* Common metrics that YOU can set up:
  * memory utilization
  * disk swap utilization
  * disk space utilization
  * page file utilization
  * log collection

* CloudWatch Dashboards
  * create dashboards for monitoring various AWS apps and environments
  * Regional or Global
* CloudWatch Alarms
  * set alarms for certain thresholds
* CloudWatch Events
  * respond to state changes in AWS resources
* CloudWatch Logs
  * help aggregate, monitor, and store logs

## CloudTrail

* AWS likes to try to confuse CloudWatch and CloudTrail on exam
* CloudTrail is like a CC TV
* CloudTrail increases visibility into user and resource activity by recording AWS Management Console actions and API calls
  * identify which users/accounts called AWS, the source IP address, and time of the calls

* CloudWatch = performance at the gym
  * network throughput or disk IO style of question
* CloudTrail = surveillance, auditing
  * who is provisioning what resource style of question

* **AWS CloudTrail is a service that enables governance, compliance, operational auditing, and risk auditing of your AWS account**

* An event in CloudTrail is the record of an activity in an AWS account
  * provide a history of both API and non-API account activity made through the AWS Management Console, AWS SDKs, command line tools, and other AWS services
  * There are two types of events that can be logged in CloudTrail:
    * management events - on by default
    * data events - not on by default

> *Back to EC2 Notes:* [**EC2 README**](./README.md)
