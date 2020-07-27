# Reliability

> **[prev]** | **[home]**  | **[next]**

👷🏻‍♂️🚧👷🏻‍♀️ (WIP)

## Shared responsibility

When you deploy applications on to Azure Platform as a Service (PaaS) we take a shared responsibility for reliability (as well as security).

For PaaS platforms, Microsoft are responsible for:

* Security, availability and compliance of the data centres, physical infrastructure, inter-region network links
* Security and reliability of the racks, servers, storage arrays, network devices
* Reliability, security patching and updates of Hypervisors, Virtual machines and their OS'es
* Reliability, security and compliance of the Platform services
* Upgrades and patching of the Platform services

Customers using PaaS plaforms are responsible for:

* Understanding the Service Level Agreement (SLA) details and failure modes for each PaaS service deployed
* Enabling reliability features to meet business requirements
* Understanding the RPO/RTO and uptime of each service deployed
* Designing solutions to avoid single points of failure
* Designing solutions with a composite SLO that meets business requirements
* Following best practices for each Platform Service
* Follow Cloud Design Patterns to increase the reliability of your solution to meet business requirements
* Taking Azure Platform and SDK updates within a reasonable period of time

## High Availability vs Disaster Recovery



## RPO, RTO, Uptime

## Well-Architected review

## Azure SLA's and uptime

Azure SLA's can be read as SLO*

An SLA is a financial guarantee, not an absolute guarantee

> 📖 [Azure Service-level Agreements]

### SLA, SLO, SLI oh my!

### Composite SLO

Pop quiz

#### SLO estimation tool


## Reliability pillar

<https://docs.microsoft.com/en-us/azure/architecture/framework/resiliency/overview>

## Reliability patterns

In the [Cloud Design Patterns] section of this 1:many session you were introduced to the patterns Microsoft have documeted in the [Azure Architecture Center]. There are two categories of Cloud Design Patterns for reliability: [Availability patterns] and [Resiliency patterns]. Of these the following are commonly used:

* **Retry**: Provides resilience to the sort of transient failures that are common in Cloud. Several Azure PaaS services require that clients retry operations and several client SDK's support this behaviour by default.
* **Circuit Breaker**: Fails fast after a configured number of _retries_. The failure signal from a circuit breaker can be used to _failover_ to a secondary connection.
* **Failover**: 
* **Queue based load levelling**: Queues also provide a convenient _Bulkhead_ to protect other components from failure.

## Failure modes

## Run books

> **[prev]** | **[home]**  | **[next]**

[prev]:./cloud-design-patterns.md
[home]:/README.md
[next]:./performance.md
[Azure Service-level Agreements]:https://azure.microsoft.com/en-au/support/legal/sla/
[Availability patterns]:https://docs.microsoft.com/en-us/azure/architecture/patterns/category/availability
[Resiliency patterns]:https://docs.microsoft.com/en-us/azure/architecture/patterns/category/resiliency
[Cloud Design Patterns]:./cloud-design-patterns.md
[Azure Architecture Center]:https://docs.microsoft.com/en-us/azure/architecture/