# Virtual Private Cloud (VPC)

## Basic Info

* exam suggestion: be able to build out a VPC by memory
* **logical data center in the cloud**
* VPC lets you provision a logically isolated section of AWS Cloud
  * within this partition, launch AWS resources in a virtual network that you define
  * have complete control over virtual network environment
    * select IP addr range
    * creation of subnets
      * build a public facing subnet for web servers = Internet access
      * backend systems on private subnet = no Internet access
      * apply NACL's and Security Groups to fine tune Security of subnets
    * configure routing tables
    * configure network gateways
* can create a Hardware VPN connection between corporate data center and VPC
  * allows you to leverage AWS Cloud as an extension of corporate Datacentero
* within each Region, 5 VPC are allowed

* **VPCs consist of:**
  * **Internet Gateway**
  * **Virtual Private Gateway**
  * Router
  * **Route Table(s)**
  * **Subnets**
    * **1 Subnet = 1 Availability Zone**
    * Can have multiple subnets in an AZ
  * **Network ACLs**
    * *Are Stateless*
  * **Security Groups**
    * *Are Stateful*
  * **Public or Private EC2 Instances**

* AWS VPC Diagram
  * Note: Bastion Host(or Jump Box) is an EC2 Instance in a public subnet which can be used to connect to an EC2 in private subnet
![VPC Diagram](../images/vpc-diagram.png)

* Internet Assisgned Numbers Authority Private Subnets
  * 10.0.0.0 - 10.255.255.255 (10/8 prefix)
  * 172.16.0.0 - 172.31.255.255 ( 172.16/12 prefix)
  * 192.168.0.0 - 192.168.255.255 (192.168/16 prefix)
  * largest subnet allowed is a /16
  * smallest subenet allowed is a /28
  > To understand CIDR and subnets a bit more: [CIDR.xyz](http://cidr.xyz/)

## VPC Uses/Actions

* launch Instances into subnet of our choosing
* assign custom IP ranges in each subnet
* configure routing tables between subnets
* create internet gateways
* much better security control over AWS resources
* assign Instance Security Groups
* subnet NACL's

## Default VPC vs Custom VPC

* default is user friendly, immediately deploy instances
  * subnets have a route out to the Internet
  * each EC2 Instance has both a public and private IP addrs
  * if default VPC is deleted, it can be recovered

## VPC Peering

* allows connection of one VPC to another via a direct network route using private IP addrs
* Instances behave like they are on same private network
* VPC peers can be within same AWS account or with other AWS accounts as well as *between Regions*
* VPC peering is always in a STAR configuration
  * 1 central VPC peers with 4 others
  * **no transitive peering**
    * two points of the star cannot go through the central point
    * if two points on the star need to communicate, they will need to have additional peer connection

> *Building a VPC Lab Notes:* [**VPC Lab Notes**](./vpc-lab-notes.md)

## Bastion Hosts

* special purpose computer on network designed and configured to withstand attacks
* computer generally hosts one a singple application
  * all other services are removed or limited to reduce threat to the computer
* Bastion Host is usually located outside of the firewall or in a DMZ and usually involves access from untrusted networks/hosts
* **Bastion Host provides a platform to SSH into the private subnet Instances**
  * enter through IGW, router, route tables, NACL, NAT Gateway, Security Group then forwards the connection to private Instance
  * hardening the bastion host is very important
  * don't have to worry about hardening devices within private subnet then
* **cannot use NAT Gateway as a Bastion Host**

## Direct Connect

* cloud service solution that makes it easy to establish a dedicated network connection from your premise to AWS
* private connection to AWS
  * reduce network costs, increase bandwidth throughput, consistent network experience
* **dedicated connection** to public and private cloud via AWS backbone that does not traverse the Internet
* **good for high throughput workloads or stable and reliably secure connection**
* Direct Connect Diagram
![Direct Connect Diagram](../images/diret-connect-diagram.png)

## VPC Endpoints

* allow a **private connection between VPC and supported AWS services and VPC Endpoint Services**
  * powered by Private Link without requiring an Internet Gateway, NAT device, VPN connection or Direct Connect
* VPC Instances do not need public IP addresses to communicate with resources in this service
* traffic between VPC and other services does not leave the AWS network
* Endpoints are **virtual devices**
  * redundant
  * highly available
  * horizontally scaled
  * allow communication between Instances in VPC and services without imposing availability risks or bandwidth constraints on network traffic

* 2 Types:
  * **Interface Endpoints**
    * Elastic network interface (ENI) with private IP address
    * serves as entry point on EC2 for traffic destined to a supported device
  * **Gateway Endpoints**
    * similar to NAT Gateways
    * supported by S3 and DynamoDB
