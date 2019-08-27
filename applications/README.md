# Application Notes

## SQS

* AWS web service that gives access to message queue that can be used to store messages while computer is processing them
* distributed queue system that quickly and reliably queue messages that one compoment in app generates to be consumed by another component
* queue = temporary repository for messages waiting to be processed
* **pull based**, not pushed based
* **256 KB message size**
* messages can be kept in queue from 1 min - 14 days
  * *default retention period = 4 days*
* **Visibility Time Out**
  * amount of time message is invisible in SQS queue after reader picks up message
  * can result in a message being delivered twice - increase time out to resolve this issue
  * timout maximum = *12 hours*
* guarantees message will be processed at least once
* AWS SQS Long Polling is a way to retrieve messages from queues
  * long polling does not return response until message arrives in queue or timeout is reached
* **message orientated API**
* way to de-couple infrastructure, if a failure it does not kill entire stack

* 2 Types of Queues:
  * **Standard** (default)
    * nearly unlimited number of transactions per second
    * guarantees message is delivered at least once
    * offer best-effort ordering which means its **ordering is not guaranteed**
    * *may have some duplicate messages*
  * **Fifo**
    * compliments Standard
    * first in first out
    * exactly-one processing
    * **order is preserved and delivered once**
    * remains available until consumer processes and deletes message
    * *duplicates are never introducted*

## Simple Work Flow Service (SWF)

* service to make it easy to coordinate work across distributed application components
* tasks represent invocations of various processing steps in an application which can be performed by executable code, web service calls, human actions, and scripts
* workflow executions can *last up to 1 year*
* **task orientated API**
* ensures task is assigned only once and is not duplicated
* keeps track of all the tasks and events in an application
* **domain refers to a collection of related workflows**

* SWF Actors
  * Workflow Starters
    * application that can initiate a workflow
  * Deciders
    * control the flow of activity tasks in workflow execution
    * if there is a failure or finished task, Decider decicdes what to do next
  * Activity Workers
    * carry out activity tasks

## Simple Notification Service (SNS)

* web service that makes it easy to set up, operate, and send notifications from the cloud
* highly scaleable, flexible, and cost-effective capability to publish messages from app  and immediately deliver to subscribers or other apps
* can deliver to SMS, email, any HTTP endpoint
* group multiple recipients based on **Topic**
  * topic = access point for allowing recipients to dynamically subscribe to identical copies of the same notification
  * one topic can support multiple deliveries to multiple endpoint types
  * SNS formats each endpoint notification appropriately
* all SNS messages are stored redundantly across multiple AZs
* Benefits of SNS:
  * instant and push based (no polling)
  * use multiple transport protocols (SES = Simple Email Service)
  * inexpensive, pay as you go
  * point and click interface
* SNS vs SQS:
  * both are messaging systems
  * SNS = push
  * SQS = polls (pull)

## Elastic Transcoder

* media transcoder in the cloud
* convert media files from original source format into different formats
* provides transcoding presets for popular output formats - no guessing
* pay based on the minutes that you transcode and the resolution at which you transcode

## API Gateway

* fully managed service that is easy to publish, maintain, monitor, and secure APIs that scale
* can act like a **front door for access to many AWS services**

* What API Gateways can do:
  * expose HTTPS endpoints to define RESTful API
  * serverlessly connect to services like Lambda and DynamoDB
  * runs efficiently with **low cost**
  * **scale effortlessly and automatically**
  * track and control usage by API key
  * **throttle requests to prevent attacks**
  * connect to **CloudWatch to log** all requests
  * maintain multiple versions of API

* How to Configure:
  * define API container
  * define resources and nested resources (url paths)
  * for each resource:
    * select supported HTTP services (verbs)
    * set security
    * set target (EC2, Lambda, DB, etc)
    * set request and response transformations

* How to Deploy:
  * deploy API to a stage
    * uses API Gateway domain name by default but it can be customized
    * now supports SSL/TLS Certs (HTTPS)

* **API Caching**
  * cache endpoint's response to increase performance
  * reduce the number of calls to endpoints and improve latency of requests made to API
  * caches for a TTL period in seconds

* Same-Origin Policy
  * important concept for web app security
  * web browser permits scripts contained in first web page to access data in a second web page but only if the web pages have the same origin
  * this is done to prevent Cross-Site-Scripting attacks (XSS attacks)
  * AWS uses a lot of different domain names = problem/concern

* **Cross Origin Resource Sharing** (CORS)
  * one way the server can relax the Same-Origin Policy
  * allows restricted resources on a web page to be requested from a different domain outside the domain from which the first request was served

## Kinesis

* **platform on AWS to send streaming data to**
* easy to load and analyze streaming data and build custom applications for business needs
* 3 Types:
  * **Kinesis Streams**
    * **stores data for 24 hours by default** but can be up to 7 days of retention
    * data is split into Shards
    * shards are sent to a service like EC2 for analyzing
    * once analyzed, data can be sent to appropriate service
    * **Shards**
      * 5 transactions per second for reads
      * data capacity of stream is a function of the number of shards that are specified for the stream
    * total capacity of stream is the sum of shard capabilities
  * **Kinesis Firehouse**
    * **no persistent storage**, data has to be analyzed as data comes in
    * can have Lambda functions inside to handle the output
  * **Kinesis Analytics**
    * works with Streams and Firehouse to analyze data on the fly inside either service

## Web Identity Federation - Cognito

* WIF give users access to AWS resources after they have successful authenticated with web-based identity provider
* after successful authentication, user receives authentication code from provider which can be used to trade AWS security creds
* AWS Cognito provides Web Identity Federation these features:
  * sing-up and sign-in for apps
  * access for guest users
  * acts as an Identity Broker between applications and Web ID providers - no additional code needed
  * synchronize user data for multiple devices
  * recommended for all mobile application AWS services

* Cognito Syncronization
  * tracks association between user identity and the user's various devices
  * provides seamless experience with Push Synchronization with updates and synchronize user data across multiple devices

* Cognito User Pools
  * are user directories used to manage sign-up and sign-in functionality for mobile and web apps
  * successful authentication generates JSON web token (JWTs)
  * handles user registration, authentication, account recovery

* Cognito Identity Pools
  * authorizes access to AWS resources
  * provide temporary AWS creds to access services like S3 and Dynamo
