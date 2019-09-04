# Serverless

## Lambda Concepts

* ultimate abstraction layer
* compute service with uploaded code
* service takes care of provisioning and managing the servers used to run code
* no need to worry about operating systems, patching, scaling, etc
* functions are independent; **1 event = 1 function**

* Lambdas used in following ways (triggers):
  * **event-driven** compute service
    * could be changes in data
  * **response-driven** compute service
    * code responds to HTTP requests using API Gateways or API calls made using AWS SDKs
  * **trigger list**
    * API Gateway
    * AWS IoT
    * Application Load Balancer
    * CloudWatch Events
    * CloudWatch Logs
    * CodeCommit
    * Cognito Sync Trigger
    * DynamoDB
    * Kinesis
    * S3
    * SNS
    * SQS
    * cannot be triggered by RDS

* 2 different requests will run 2 different Lambda processes, does not need to queue

* **Traditional vs Serverless Architecture**
  * Traditional possible scenario = hit Load Balancer -> web server -> backend RDS Instance -> response to user
    * running on virtual machines
  * Serverless possible scenario = hit API Gateway -> Lambda -> DB Instance -> response to user
    * instant scaling if suddenly a million requests are coming in

* Supported Languages
  * Node.js
  * Java
  * Python
  * C#
  * Go
  * Powershell

* Pricing
  * based on number of requests
    * first million are free
    * $0.20 per 1 million thereafter
  * based on duration
    * calculated based on time code begins executing until it returns or otherwise terminates
    * rounded up to nearest 100ms
    * also based on amount of memory allocated to function
    * $0.000001667 for every GB-second used

* Benefits
  * no servers
  * continuous scaling
  * super cheap
  * **scales out not up automatically**

* **AWS X-ray helps to debug Lambda functions**
* Lambda@Edge allows Lambda functions in AWS locations closer to users to decrease latency
