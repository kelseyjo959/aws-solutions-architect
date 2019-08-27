# High Availability Architecture

## Load Balancers

* physical or virtual device designed to help balance network load across multiple network servers
* 3 Types:
  * **Application Load Balancer**
    * best for HTTP/S traffic
    * operate at Layer 7 and are application aware
    * *intelligent* with advanced request routing
  * **Network Load Balancer**
    * best for TCP traffic where *extreme performance* is required
    * operate at Layer 4
    * can handle millions of requests per second while maintaining ultra-low latency
  * **Classic Load Balancer**
    * legacy ELB
    * can balance both Layer 4 or 7
    * not intelligent, good if you don't care how traffic is routed

* 504 error = means gateway timeout, application or database is having an issue

* **x-forwarded-for header**
  * way to get user's IP address as it has passed through the load balancer

