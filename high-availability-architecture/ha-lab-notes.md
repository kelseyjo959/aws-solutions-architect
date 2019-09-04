# High Availability Lab Notes

## Load Balancers and Health Checks

* create Load Balancer under EC2 Instance
* assign Security Group
* configure health check
  * timeout = time to wait for the response of health check
  * interval = amount of time between checks
  * threshold = number of unhealthy failures before declaring EC2 unhealthy status
* assign which EC2 Instances to receive Load Balancer
* **never given an IP for an Load Balancer**
  * must use the DNS record to browse to the web server
* Instances monitored by ELB are reported as either:
  * *InService*
  * *OutofService*

## Auto Scaling Groups

* need a Launch Configuration first
  * making this configuration doesn't do anything but sets up for when new Instances are needed for scaling purposes
* ASGs are for scaling out
* schedule Auto Scaling when increased usage is expected
* default ASG termination policies:
  * if Instances are in multiple AZs, AZ with most Instances and with the oldest launch configuration
  * determine if there is an unprotected Instance, terminate that one
  * if multiple unprotected Instances, terminate one that is closest to nearest Billing Hour
  * if there are multiple close to the same Billing Hour, pick at random

> *Back to HA Notes* [HA Notes](./README.md)
