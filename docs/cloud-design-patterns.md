# Cloud design patterns

> **[prev]** | **[home]**  | **[next]**

The Azure Architecture Center contains a large number of design patterns that explain how common
problems can be solved with cloud architecture. There are a large number of patterns that span
several types of considerations including reliability, performance, and managing complex
deployments.

In this section we will briefly examine a few of the patterns that relate to the fundamental
concepts we explored in the previous section.

> 📖 See all of the design patterns in the [Azure Architecture Center's design patterns list].

## Patterns to support cost optimisation

### Static Content Hosting pattern

The relative cost of storage is much lower than that of compute resources. One way to exploit this
is to move static content into a storage system, or to use caching (e.g. Azure CDN) to store and
re-serve data that does not change frequently. This is also a great way to increase the performance
of an application by serving it from resources that are geographically closer to users, and by
offloading the processing of these requests to dedicated services that are optimised for this task.

> 📖 Read the full [Static Content Hosting pattern].

### Compute Resource Consolidation pattern

Increase the resource utilisation of compute resources by combining multiple workloads onto a single
set of resources. This works particularly well for components that do not support high scale or have
high resource requirements.

> 📖 Read the full [Compute Resource Consolidation pattern].

## Patterns to support elasticity and loose coupling

### Async Request-Reply pattern

Avoid having frontend hosts performing long-running tasks. Instead, have the frontend host initiate
a background processor to complete the task, and allow the client to obtain the status of the task.

> 📖 Read the full [Async Request-Reply pattern].

### Publisher-Subscriber pattern

Have application components publish messages into a message broker (often a queue, but not
necessarily). Consumers then subscribe to that broker and receive messages as they are available.

> 📖 Read the full [Publisher-Subscriber pattern].

### Queue-based Load Leveling pattern

Once a queue is employed (e.g. as per the [Publisher-Subscriber pattern]), the system processing
messages from the queue can process at a consistent rate. This supports elastic scaling since new
workers can be provisioned and deprovisioned based on queue length.

> 📖 Read the full [Queue-based Load Leveling pattern].

### Competing Consumers pattern

Multiple workers can subscribe to a single queue. They 'compete' for messages, letting the queue
deliver messages to each one, and can obtain further messages as they complete the processing of
each message. This helps to balance the workload between workers.

> 📖 Read the full [Competing Consumers pattern].

## Patterns to support eventual consistency

### Compensating Transactions pattern

Eventually consistent systems can make it difficult or impossible to roll back failed transactions.
Instead, implement a transaction that undoes the effect of the failed transaction while taking
account of any subsequent actions that may have taken place.

> 📖 Read the full [Compensating Transactions pattern].

### Choreography pattern

Have multiple systems independently perform operations based on messages or events. Instead of
having a single controller orchestrating everything, have each sub-component or microservice make
its own decisions and perform its own operations. Each independent system may be processing data at
different rates, and therefore may not have strong consistency with one another.

> 📖 Read the full [Choreography pattern].

## Patterns to support partitioning

## Sharding pattern

Divide data sources into horizontal partitions (shards) and store them in distinct databases or
stores. This enables high levels of scale-out across independent sets of compute and storage
resources.

> 📖 Read the full [Sharding pattern].

## Deployment Stamps pattern

Deploy multiple instances of your solution, including compute resources and dedicated data stores.
Direct specific customers (tenants) to specific stamps. This allows for running independent copies
of your solution in different geographical regions, as well as running single- and multi-tenant
instances.

> 📖 Read the full [Deployment Stamps pattern].

## Patterns to support reliability and resiliency
* [Thottling pattern]:https://docs.microsoft.com/en-us/azure/architecture/patterns/throttling
* [Retry pattern]:https://docs.microsoft.com/en-us/azure/architecture/patterns/retry
* [Circuit Breaker pattern]:https://docs.microsoft.com/en-us/azure/architecture/patterns/circuit-breaker

> **[prev]** | **[home]**  | **[next]**

[prev]:/cloud-fundamentals.md
[home]:/README.md
[next]:./reliability.md
[Azure Architecture Center's design patterns list]:https://docs.microsoft.com/en-us/azure/architecture/patterns/
[Static Content Hosting pattern]:https://docs.microsoft.com/en-us/azure/architecture/patterns/static-content-hosting
[Compute Resource Consolidation pattern]:https://docs.microsoft.com/en-us/azure/architecture/patterns/compute-resource-consolidation
[Async Request-Reply pattern]:https://docs.microsoft.com/en-us/azure/architecture/patterns/async-request-reply
[Publisher-Subscriber pattern]:https://docs.microsoft.com/en-us/azure/architecture/patterns/publisher-subscriber
[Queue-based Load Leveling pattern]:https://docs.microsoft.com/en-us/azure/architecture/patterns/queue-based-load-leveling
[Competing Consumers pattern]:https://docs.microsoft.com/en-us/azure/architecture/patterns/competing-consumers
[Choreography pattern]:https://docs.microsoft.com/en-us/azure/architecture/patterns/choreography
[Compensating Transactions pattern]:https://docs.microsoft.com/en-us/azure/architecture/patterns/compensating-transaction
[Sharding pattern]:https://docs.microsoft.com/en-us/azure/architecture/patterns/sharding
[Deployment Stamps pattern]:https://docs.microsoft.com/en-us/azure/architecture/patterns/deployment-stamp
