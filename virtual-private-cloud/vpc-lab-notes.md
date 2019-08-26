# VPC Lab Notes

* VPC is under `Networking & Content Delivery`
* `Tenancy` - chose whether VPC will be on Dedicated hardware or not (dedicated = $$$)
  * default = multi-tenant
* **upon creation of a VPC additional settings automatically set or not set:**
  * a Route Table will be created
  * NACL is created
  * Security Group created
  * Internet Gateway is NOT created
  * Subnets are NOT created

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
