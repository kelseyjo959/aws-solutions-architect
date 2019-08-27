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
  * can result in a message being delivered twice
  * timout maximum = *12 hours*
* guarantees message will be processed at least once
* AWS SQS Long Polling is a way to retrieve messages from queues
  * long polling does not return response until message arrives in queue or timeout is reached
* **message orientated API**

* 2 Types of Queues:
  * **Standard** (default)
    * nearly unlimited number of transactions per second
    * guarantees message is delivered at least once
    * offer best-effort ordering which means its ordering messages the best it can
    * *may have some duplicate messages*
  * **Fifo**
    * compliments Standard
    * first in first out
    * exactly-one processing
    * order is preserved and delivered once
    * remains available until consumer processes and deletes message
    * *duplicates are never introducted*

## Simple Work Flow Service (SWF)

* service to make it easy to coordinate work across distributed application components
* tasks represent invocations of various processing steps in an application which can be performed by executable code, web service calls, human actions, and scripts
* workflow executions can *last up to 1 year*
* **task orientated API**
* ensures task is assigned only once and is not duplicated
* keeps track of all the tasks and events in an application

* SWF Actors
  * Workflow Starters
    * application that can initiate a workflow
  * Deciders
    * control the flow of activity tasks in workflow execution
    * if there is a failure or finished task, Decider decicdes what to do next
  * Activity Workers
    * carry out activity tasks


