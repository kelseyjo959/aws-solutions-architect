# Domain Name Service (DNS)

## Basic Info

* AWS DNS = Route53
* DNS converts human readable domain names to an IP address
  * can be IPv4 or IPv6
* IPv4 is running out of addresses - only 4 billion
* IPv6 has 340 undecillion addresses
* last set of letters witin a domain name are the top level domain
  * there can also be a second set that is the second level domain
    * gov.uk
    * com.au
* top level domains controlled by the Internet Assigned Numbers Authority (IANA)
  * root zone database = database of all available top level domains
* **Elastic Load Balancers do not have pre-defined IPv4 addresses, always resolve to a DNS name**
* **Health Checks**
  * can be set on individual record sets
  * if record set fails a health check it will be removed from Route53 until it passes
  * set up SNS alerts for failed health checks
* There is a limit (50) to the number of domain names that you can manage using Route 53
  * however, contacting AWS support can increase that number

## Domain Registrar

* authority that can assign domain names directly under one or more top level domains
* domains registered with InterNIC which is a service of ICANN
  * ICANN enforces uniqueness of domain names across internet
* WhoIS database = central database of all domain names

## DNS Types

* SOA Records
* NS Records
* A Records
* CNAMES
* **MX Records** - used for mail
* **PTR Records** - reverse of A Record, look up name against an IP address

## SOA

* a Domain Name will have a Start Of Authority (SOA) record
  * Stored info:
    * name of server that supplied the data for zone
    * admin of the zone
    * current version of data file
    * default number of seconds for time-to-live file on resource records

## NS

* Name Server Records
* used by Top Level Domain servers to direct traffic to the Content DNS server which contains the authoritative DNS records
* query the NS Record to get the SOA

## A Record

* "A" Record is the fundamental type of DNS record
* A is for Address
* A record is used to translate the name of the domain to an IP address

## TTL

* Time to Live in seconds
* length that a DNS record is cached on the Resolving Server or local host
* the lower the time, the faster changes to DNS records can propagate throughout the internet
  * default can usually be 48 hours

## CNAME

* Canonical Name
* used to resolve one domain name to another
  * phonebook example = "Batman" maps to "Adam West"
* cannot be used for naked domain names (zone apex record)

## Alias Record

* used to map resource record sets in hosted zone to Elastic Load Balancers, CloudFront Distributors, or S3 configured as website
* work like CNAME record in that you can map one DNS name to another target DNS name
* given the choice, choose Alias Record over CNAME

* **know the difference between CNAME and Alias Record**

## Routing Policies

* **Simple Routing**
  * can only have **one record with multiple IP addresses**
  * all values return randomly
  * no health checks
* **Weighted Routing**
  * **split traffic based on weight assigned**
  * health checks can be set on individual record sets
    * if a health check fails, the record will be removed from Route53 until it passes health check again
    * can set SNS notifications to get alert of health check failure
* **Latency Routing**
  * route traffic based on **lowest network latency for the user** (which Region gives fastest response time)
* **Failover Routing**
  * used for **active/passive** set up for disaster recovery
    * Route53 will monitor health of primary using Health Check (monitors the end points)
* **Geolocation Routing**
  * choose where traffic will be sent based on geographic location of users
    * this location will be where DNS queries originate
* **Geoproximity Routing** (Traffic Flow Only)
  * route traffic **based on geographic location of users AND resources**
  * can also tweak how much traffic goes to which location  = bias
    * bias expands or shrinks geographic region
  * **Route53 Traffic Flow must be used**
* **Multivalue Answer Routing**
  * configure Route53 to return multiple values
    * values like IP addresses for web servers in response to DNS queries
    * can also get the health check of each resource
      * only return values of healthy resources
    * **similar to Simple Routing but it allows for health checks on each record set**
