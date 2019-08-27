# VPC Lab Notes

* VPC is under `Networking & Content Delivery`
* `Tenancy` - chose whether VPC will be on Dedicated hardware or not (dedicated = $$$)
  * default = multi-tenant
* **upon creation of a VPC additional settings automatically set or not set:**
  * a Route Table will be created
  * NACL is created
  * Security Group created
  * Internet Gateway is *NOT* created
  * Subnets are *NOT* created

* **Security Groups do not span VPCs**
* **us-east-1a is not going to be the same in a different AWS account, AWS randomizes the AZs**

* Creating a Subnet
  * can chose AZ
  * pick subnet block with CIDR notation
  * name tag - example = `10.0.1.0 - us-east-2a`
  * optional IPv6 addr block
  * of a reserved block of addresses, **AWS will use 5 of them for the following**:
    * Network address - 10.0.0.0
    * VPC router - 10.0.0.1
    * VPC DNS Server - 10.0.0.2
    * AWS Future proofing 10.0.0.3
    * Network Broadcast Address - 10.0.0.255 (broadcast is not supported in VPC)

* Making Subnet Public
  * Action = `modify auto-assign IP settings`
    * enable with checkbox

* Create Internet Gateway
  * upon creation, state = detached
  * Action = `Attach to VPC`
  * **only 1 Internet Gateway per VPC**
  * AWS designed Internet Gateways to be highly available

* Configure Route Table
  * `Create Route Table`
  * For Route OUT:
    * `Edit Routes` with `0.0.0.0/0`, chose Internet Gateway
  * any subent associated with this route table will then be public

* Accessing Private VPC subnet
  * Create new Security Group for the EC2 Instance
  * Pick the VPC the Instance is in
  * Types
    * All ICMP, Source = CIDR range of public subnet or specific Security Group
    * allow HTTP, HTTPS, SSH

## NAT Instances & NAT Gateways

* Network Adress Translation
* a way for private subnets to go out and download software from the Internet
* **NAT Instances are EC2 Instances that handle the network address translation**
* **NAT Gateways are spread across multiple AZ, highly available, not dependent on a single Instance**
* NAT Gateways start at 5Gbps and scale to 45Gbps - **scales automatically**
* **NAT Gateways are redundant inside the AZ**

* Launch NAT Instance
  * Launch EC2 Instance - community AMIs
  * NAT type - free tier
  * Network = pick your VPC
  * Launch into **public subnet**
  * **need to disable source/destination check on the Instance**
  * once NAT Instance is set up, add it to VPC Route Table
    * add route from private instance to NAT Instance IP
  * **always behind a Security Group**
  * NAT Instance is a networking bottle neck
    * can get around this with bigger Instance size
    * Autoscaling Groups, multiple subnets in different AZs but these are all a pain
  * being phased out

* Launch new NAT Gateway
  * `NAT Gateways` in VPC Menu
  * create in public subnet (based on subnet id)
  * need to edit route table to point at new gateway
    * give route out to 0.0.0.0/ with target of NAT gateway
  * **not associated with Security Groups**
  * **autmatically assigns public IP addr**
  * **no need to disable Source/Destination checks**

## NACls vs Security Groups

* **VPC automatically comes with default NACL which allows all inbound/outbound traffic**
* create new NACL
  * pick VPC
  * **upon NACL creation, Inbound and Outbound rules automatically deny everything**
  * AWS suggests grouping rules in the 100s
    * allow IPv4 = rule 100
    * allow IPv6 = rule 101
    * for outbound rules sometimes use ephemeral ports rathern than specific ports
      * 1024 - 65535 - used by NAT Gateway
      * used on the server end of a communication
    * Allow/Deny occur in chronological order
      * If an allow occurs before the deny, traffic is still allowed

* NACLs trump Seucurity Groups
* NACLs can block IP addresses, Security Groups cannot
* **subnet can only be associated with one NACL at a time**
  * if not assigned, it will always be assigned to the default NACL that comes with creation of VPC

## VPCs with ELB

* **when creating an ELB, you need to have at least 2 public subnets**

## VPC Flow Logs

* enables capturing of info about IP traffic going to and from network interface within VPC
* stored using AWS CloudWatch Logs
  * once a log is created, can retreive that data within CloudWatch
* Can be created at 3 levels:
  * VPC
  * subnet
  * network interface level
* Action `Create Flow Log`
  * need a new CloudWatch log group to assign flow log to
* **once created, you cannot change its config**
* **cannot tag a flow log**
* **not all IP traffic is logged**
  * Instance communication with AWS DNS is not logged
  * if using own DNS server, this traffic IS logged
  * traffic meta data not logged
  * windows license activation not logged
  * DHCP is not logged
  * AWS reserved IP addrs not logged

## VPC Endpoints

* must have an S3 IAM role for EC2 Instance
* add role to EC2 Instance in private subnet
* SSH into EC2 Instance 
* remove route to NAT gateway (removes access to outside Internet)
* `VPC EndPoint` in VPC Dashboard
  * choose AWS service
  * add to main route table
  * `aws s3 ls -- region` + region_name

> *Back to VPC Notes* [VPC Notes](./README.md)
