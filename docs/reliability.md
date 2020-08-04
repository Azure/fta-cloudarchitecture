# Reliability

> **[prev]** | **[home]**  | **[next]**

> 📖 Follow the guided learning path for Reliability in **[Microsoft Azure Well-Architected Framework - Reliability]** (Microsoft Learn)

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

Definitions for High availability (HA) and Disaster recovery (DR) can vary from organisation to organisation and even from team to team. The Well Architected Framework focuses on _Reliability_ as an overarching theme to include important aspects from an HA design and a DR strategy to achieve the desired RTO, RPO and uptime.

Architecting for reliability ensures that your application can meet the commitments you make to your customers. This includes ensuring that your systems are _available_ to end users and can _recover_ from any failures.

## RTO, RPO, Uptime

Every application, service, platform and system has a stated or implied RTO, RPO and uptime. 

**Uptime**: The target uptime for the system usually measured as a percentage. For example, [99.9% uptime] equates to 43 minutes and 49 seconds of downtime per month. "Downtime" can be measured in various ways, but usually means that the service is not responding to repeated requests.

**Recovery time objective (RTO)**: The maximum duration of acceptable downtime, where "downtime" is defined by your specification. For example, if the acceptable downtime duration is eight hours in the event of a disaster, then your RTO is eight hours.

**Recovery point objective (RPO)**: The maximum duration of acceptable data loss. RPO is measured in units of time, not volume. Examples are "30 minutes of data," "four hours of data," and so on. RPO is about limiting and recovering from data loss, not data theft.

## Azure Service-level agreement's

> 📖 Familiarize yourself with **[Azure Service-level Agreements]**.

> 📺 Watch [SLIs, SLOs, SLAs, oh my!] for a definition of these terms and an explanation of the differences.

* An Azure Service-level Agreement (SLA) can also be read as a minimum Service-level Objective (SLO).
* An SLA is a financial guarantee, not an absolute guarantee
* Read the SLA details carefully, particularly the definition of "Downtime" for each service, which give important hints about _Failure modes_

For example, in the [SLA for Azure SQL Database], "Downtime" is:

_"The total accumulated Deployment Minutes across all Databases in a given Microsoft Azure subscription during which the Database is unavailable. A minute is considered unavailable for a given Database if **all continuous attempts by Customer to establish a connection to the Database** within the minute fail."_

The Azure SQL Database team expect almost all outages to be transient (brief and non-recurring). Therefore the _Retry_ pattern should be used to continuously retry for up to a minute. This is typical in cloud services; retry has been the default behaviour in ADO.NET since .NET Framework 4.6.1.

## Determine the SLA of your application

> 📖 Study [Determine the service-level agreement of your application] on Microsoft Learn

RTO, RPO and uptime are important business (non-functional) requirements. It is important the business are consulted when determining these requirements. There is a strong relationship between uptime, complexity and cost for example.

## Architecture review

Once the target SLA requirements have been determined an _Architecture review_ should be performed to ensure that these requirements are met. 


> 💡 The **FastTrack for Azure** team can perform an architecture review of your solution on behalf of Azure Engineering. Visit [Microsoft FastTrack for Azure] to learn more about FastTrack.

### Composite SLA

It is important to review the SLA's of the solution as a whole, as well as the SLA's for individual services. Annotate the solution architecture diagram with SLA, RTO and RPO for all components. Single points of failure should be called out, and the composite SLA for the solution should be calculated by combining the SLA for each service.

As an example, the [API-first SaaS business model] reference architecture has been annotated with uptime, RTO and RPO figures below.

![Annotated AKS API First reference architecture](./images/annotated-aks-api-first.png) <br/> _Figure: Annotated API-first SaaS business model reference architecture_

The uptime SLA's for each component in the _critical path_ of a solution should be multiplied together to calculate the _composite SLA_.

**Q. What is the composite uptime SLA for the solution above?** (From the point of view of an API user)

1. 99.995%?
1. 99.9%?
1. Less than 99.9%?

How could the uptime be improved?

> 🔨 Use the **[Composite SLO Estimation spreadsheet]** to calculate composite SLO

> 📖 See also: [FastTrack for Azure Architectural / Solution Review and Guidance Framework]

## Availability and recovery features

Azure PaaS services provide _features_ for availability and recovery. Some features are only available in certain SKUs or Tiers (e.g. Premium). Some features are provided by [Zonal or zone-redundant architecture] in Availability Zones (AZ's). For example:

| Service | HA features | Recovery features | AZ support |
| ------- | ----------- | ----------------- | ---------- |
| Azure App Services | <ul><li>[99.95% uptime](https://azure.microsoft.com/en-au/support/legal/sla/app-service/v1_4/)</li><li>[Deployment (Swap) Slots]</li></ul> | [Scheduled backups](https://docs.microsoft.com/en-us/azure/app-service/manage-backup#configure-automated-backups) | [Zonal for ASE's](https://docs.microsoft.com/en-us/azure/app-service/environment/zone-redundancy) |
| Azure SQL DB | <ul><li>[Uptime SLA](https://azure.microsoft.com/en-au/support/legal/sla/sql-database/v1_4/) of between 99.9% and 99.995% depending on SKU, tier and configuration.</li><li>[Active Geo replication](https://docs.microsoft.com/en-us/azure/azure-sql/database/active-geo-replication-overview)</li><li>[Failover groups](https://docs.microsoft.com/en-us/azure/azure-sql/database/auto-failover-group-overview?tabs=azure-powershell)</li></ul> | [Automated backups and Point in time restore](https://docs.microsoft.com/en-us/azure/azure-sql/database/automated-backups-overview?tabs=single-database) | Zone redundant |
| Azure API Management | <ul><li>[99.95% uptime SLA](https://azure.microsoft.com/en-au/support/legal/sla/api-management/v1_4/)</li><li>99.99% uptime with [multi-region deployment](https://docs.microsoft.com/en-us/azure/api-management/api-management-howto-deploy-multi-region)</li></ul> | [Backup & restore](https://docs.microsoft.com/en-us/azure/api-management/api-management-howto-disaster-recovery-backup-restore) | 




Geographical locations (Single region / multi-region)
Recovery Time Objective (RTO)
Recovery Point Objective (RPO)

## Well-Architected review


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

👷🏻‍♂️🚧👷🏻‍♀️ (WIP)

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
[Microsoft Azure Well-Architected Framework - Reliability]:https://docs.microsoft.com/en-us/learn/modules/azure-well-architected-reliability/
[99.9% uptime]:https://uptime.is/99.9
[Determine the service-level agreement of your application]:https://docs.microsoft.com/en-us/learn/modules/azure-well-architected-reliability/2-high-availability#determine-the-service-level-agreement-of-your-application
[SLIs, SLOs, SLAs, oh my!]:https://www.youtube.com/watch?v=tEylFyxbDLE
[SLA for Azure SQL Database]:https://azure.microsoft.com/en-au/support/legal/sla/sql-database/v1_4/
[FastTrack for Azure Architectural / Solution Review and Guidance Framework]:https://github.com/Azure/fta-architecturalreview/blob/master/articles/introduction.md
[Microsoft FastTrack for Azure]:https://azure.microsoft.com/en-us/programs/azure-fasttrack/
[Composite SLO Estimation spreadsheet]:/tools/Composite_SLO_Estimation_Tool.xlsx
[Zonal or zone-redundant architecture]:https://docs.microsoft.com/en-us/azure/architecture/high-availability/building-solutions-for-high-availability#zonal-vs-zone-redundant-architecture
[Deployment (Swap) Slots]:https://docs.microsoft.com/en-us/azure/app-service/deploy-staging-slots#swap-two-slots
[API-first SaaS business model]:https://docs.microsoft.com/en-us/azure/architecture/solution-ideas/articles/aks-api-first