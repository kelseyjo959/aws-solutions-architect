# Snowball

* petabyte-scale data transport solution in **disk format**
* uses secure appliance to **import or export data to AWS S3**
* solves high data transfer issues:
  * high network costs
  * long transfer times
  * security concerns
* simple, fast secure process as little as 1/5th the cost of high speed internet
* 50TB or 80TB
* Security:
  * tamper-resistant enclosure
  * 256-bit encryption
  * industry standard TMP (Trusted Platform Module) that ensure secuity and full chain-of-custody of data
  * upon completion of transfer, AWS performs a software erasure of Snowball appliance

* Snowball Edge
  * 100TB with onboard storage and compute properties
  * move LARGE amounts of data
  * temporary storage tier for large local datasets
  * support local workloads in remote or offline locations
  * connects to existing applications/infrastructure
  * can be clustered to form local storage tier

* Snowmobile
  * Exabyte-scale data transfer service used to move REALLY LARGE amounts of data
  * up to 100PB per Snowmobile
  * 45 foot long truck with ruggidized shipping container
  * great for video libraries, image repos, complete data centers

* When to use Snowball
  * Internet connection: T3
  * No. of theoretical days of network utilization: 269
  * when to use Snowball = 2TB or more

  * Internet connection: 100Mbps
  * No. of theoretical days of network utilization: 120
  * when to use Snowball = 5TB or more

  * Internet connection: 1000Mbps
  * No. of theoretical days of network utilization: 12
  * when to use Snowball = 60TB or more

  > *Back to S3 Notes:* [S3 README](./README.md)
