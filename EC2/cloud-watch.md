# CloudWatch

* Monitoring service for monitoring AWS resources as well as AWS applications
* create CloudWatch alarms that trigger notifications
* **Standard Monitoring = 5 mins**
* **Detailed Monitoring = 1 min**
* Performance Monitoring of:
  * Compute
    * EC2
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
* CloudTrail inceases visibility into user and resource activity by recording AWS Management Console actions and API calls
  * identify which users/accounts called AWS, the source IP address, and time of the calls

* CloudWatch = performance at the gym
  * network throughput or disk IO style of question
* CloudTrail = surveliance, auditing
  * who is provisiong what resource style of question

> *Back to EC2 Notes:* [**EC2 README**](./README.md)
