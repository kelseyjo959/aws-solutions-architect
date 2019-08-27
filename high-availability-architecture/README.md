# High Availability Architecture

## Load Balancers

* physical or virtual device designed to help balance network load across multiple network servers
* 3 Types:
  * **Application Load Balancer** (ALB)
    * best for HTTP/S traffic
    * operate at *Layer 7* and are application aware
    * *intelligent* with advanced request routing
  * **Network Load Balancer** (NLB)
    * best for TCP traffic where *extreme performance* is required
    * operate at *Layer 4*
    * can handle millions of requests per second while maintaining ultra-low latency
  * **Classic Load Balancer**
    * legacy ELB
    * can balance both Layer 4 or 7
    * not intelligent, good if you don't care how traffic is routed
    * routes each request independently with smallest load

* *504 error* = means gateway timeout, application or database is having an issue

* **x-forwarded-for header**
  * way to get user's IP address as it has passed through the load balancer

## Advanced Load Balancing

* **Sticky sessions** allow one to bind user's session to a specific EC2 Instance
  * ensures all requests from user during session are sent to the same Instance
  * can be enabled for for Application Load Balancer but the traffic will be sent to Target Group Level

* **Cross Zone Load Balancing**
  * enables balancing traffic between two different AZ so that traffic is more evenly distributed

* **Path Patterns**
  * create a listener with rules to forward requests based on URL path
  * known as path-based routing
  * running microservices, can route traffic to multiple back-end services

* [ELB FAQ](https://aws.amazon.com/elasticloadbalancing/faqs/)

## CloudFormation

* way to completely script cloud environment
* Quick Start is a bunch of CloudFormation templates already built by AWS to create complex environments quickly

## Elastic Beanstalk

* quickly deploy and manage applications in AWS Cloud without worrying about infrastructure
* simply upload application, and automatically handles details of capacity provisioning, load balancing, scaling, and app health monitoring

> *HA Lab Notes* [HA Lab Notes](./ha-lab-notes.md)
