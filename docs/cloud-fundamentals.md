# Cloud fundamentals

> **[prev]** | **[home]**  | **[next]**

Digital transformation has driven incredible demand for services and the servers that host them. The
cloud is essentially a solution to problems of economics and scale in server hosting. As a result of
the change in scale, we need to design and architect our systems specifically so that we can make
the most of the infrastructure available.

The cloud has changed the way we think about architecting solutions. Cloud providers like Azure have
enormous pools of compute resources and storage, vast global networks, and handle a significant
amount of the administrative and management burden for you. There are a few principles you should
think about as you design your solution so that you can get the most out of being in the cloud.

## Economics of the cloud

In traditional models of server hosting, we typically maintained corporate server rooms and small
data centres to house our infrastructure. Equipment was procured, installed, and then operated for
a fixed lifetime - usually three to five years - before being decommissioned and replaced. This
required capital expenditure of fixed cost, and the asset values depreciated over time. Traditional
hosting models also favoured manual operations and often had fairly relaxed security.

Virtualisation helped to get more efficient use of our infrastructure, since we could provision
capacity and spread it across multiple workloads. But for most companies it was challenging to
achieve optimal density of VMs to hosts due to the [knapsack problem]. Scaling VMs up often requires
even more infrastructure to be provisioned.

The cloud is essentially a hyperscale virtualisation environment. Cloud regions (comprised of
multiple datacentres) can host millions of cores and petabytes of RAM and storage. As there are so
many resources available, the law of large numbers dictates that we can achieve better density and
can generally have a much better chance of fulfilling scale requests. The economies of scale also
mean that the average marginal cost (of additional CPU/RAM/storage) can often be much lower in the
cloud.

### Relative cost of resources

Different types of resources have very different pricing models. Consider four common types of
resources used in many cloud-hosted applications:

* Network traffic. Azure typically does not charge for traffic entering our regions (ingress) but
  does charge for traffic as it leaves (egresses) our regions.
* Storage. There are a number of different storage options for different storage profiles.
* Compute. There are a large number of options for types of VMs available depending on the feature
  set and resource profile required.
* A SQL database, which includes storage, compute, and networking as part of its implementation.

We can compare the relative costs of some entry-level resource profiles for each of these resource
types:

![Relative cost of resources](./images/relative-costs.png)<br/>_Figure: Relative cost (approximate)
of resources in Azure._

These prices are not expensive in absolute terms, but the explicit pricing models mean that we can
track our expenditure on different resources and ensure we are using them as efficiently as
possible.

This is particularly important when we operate at high scale. Large software vendors (e.g.
Microsoft, Google, and Facebook) make use of architectures and patterns that favour less expensive
resources while still achieving massive scale. We can use similar practices to optimise the
selection of technologies to suit the cloud pricing models.

> 📖 Read more in [Azure Well-Architected Framework - Maximize efficiency of cloud spend]
> (Microsoft Learn)

### Cloud models

TODO
Self-managed vs. managed, IaaS/PaaS/serverless
Consider the TCO - the cloud vendor is taking a lot of the work away from you

## Elasticity

There are a number of workload patterns that make the best use of the economics and scale of the
cloud:

* **On and off:** some workloads only need to run for a small amount of time, such as batch jobs.
  Provisioning dedicated infrastructure just for these is wasteful when the infrastructure is only
  used intermittently.
* **Growing fast:** workloads that scale up as the business grows will require more and more
  infrastructure to run them. Without the cloud, it can be very hard to provision new hardware fast
  enough to keep up with growing demand.
* **Unpredictable bursting:** some workloads have unpredictable or unplanned burst in demand, such
  as when a celebrity endorses a product on Twitter. Sudden spikes in load can impact performance
  for everyone, and since the bursting is unpredictable we need the elasticity of the cloud in order
  to rapidly provision new resources.
* **Predictable bursting:** even when a workload's bursting is predictable and planned, such as
  daily or seasonal peaks in traffic, it can be challenging to provision enough capacity for those
  times while not wasting resources the rest of the time. The elasticity of the cloud allows for the
  necessary resources to be provisioned when needed and then deprovisioned.

![Cloud computing patterns](./images/cloud-computing-patterns.png)<br/>_Figure: Common workload
patterns for the cloud._

Each of these take advantage of **elasticity** - the ability to rapidly provision new resources.
The large pool of resources made available by cloud providers means that new resources can be
provisioned when they are required, used for as long as they are needed, and then deprovisioned.

By taking advantage of elasticity you can keep your costs low initially as you build out your
user base, while also rapidly responding to an influx of traffic or activity.

To make the most of the elasticity provided by the cloud there are a few things you can do such as:
* Prefer stateless applications wherever possible, so that you can rapidly shift your traffic
  around and don't have to pin specific requests to specific compute instances.
* Avoid having bottlenecks that might inhibit your ability to scale out quickly.
* Loosely couple your components so that you can scale each part of your solution independently.
* Configure [auto-scaling] on your resources so that you can quickly scale even with unpredictable
  bursting.

> 📖 Read more in [Azure Architecture Guide - Design to scale out]

## Loose coupling
Any non-trivial solution will be made up of multiple components that work together. The
communication and coupling between these components matters a great deal.

Synchronous communication is often the simplest approach to implement. It also is typically very
performant, since messages are sent directly from point to point. This can be a good approach for
simpler systems, or for communicating between two parts of a solution that are highly
interdependent - for example, talking from an application to a database or cache.

However, in some situations tight coupling will lead to problems. Any downstream delays, failures,
or bottlenecks can cause your entire solution's performance to be degraded. Also, tight coupling
means that the sender needs to know the exact location to send a request to (e.g. an IP address,
port, or hostname). If we are using horizontal scaling in our solution then it can be difficult to
keep track of which compute nodes might currently be running the component we need to talk to.

Loose coupling, on the other hand, typically involves asynchronous communication. It often makes
use of message brokers like Service Bus. Instead of sending requests directly between systems, the
sender might instead sends a message to a broker and the destination system subscribes to the same
broker. Messages are delivered through the broker, and regardless of how many instances of the
sender or receiver there may be, the broker will handle reliable delivery to the correct recipients.
One example of this type of design is the [Web-Queue-Worker architecture style].

Another alternative, the [event-driven architecture style], can be used for components to publish
information about actions that have taken place into a central event store. Other components can
listen to the events coming from that store, and can decide independently when they might want to
take action.

Loose coupling has some important benefits for resiliency and elasticity.
* **Resiliency:** loose coupling means there is a buffer between your solution components to
  protect them one another's failures. This typically increases the resiliency of the overall solution.
* **Elasticity:** to achieve elastic scale, it helps to have loosely coupled components. Adding
  additional compute workers and removing unnecessary compute workers can be achieved without
  upstream systems needing to be aware of the scaling.

> 📖 Read more in [Application Architecture Guide - Minimize coordination]

## Eventual consistency

TODO
* Historically, applications have been built to expect their data stores to have strong consistency - i.e. to have the most recent data available at all times, and for changes to data to be instantly persisted and available everywhere
* Cloud-based systems often need networking across geographical distances, and geographic networking means latency
* Strong consistency also imples tight coupling
* If you are using strong consistency, you need to synchronously update data stores and wait for confirmation - this could be very slow in a geo-replicated data store
* Instead we think about eventual consistency where possible - systems will coordinate with one another and will eventually be in sync, but for some period (usually seconds or minutes, sometimes longer) they might be out of sync with recent changes
* Sounds bad, but it's actually quite workable - e.g. for sales data, you typically need up to midnight the night before, not up-to-the-second accuracy
* Many solutions need a mixture of strong and eventual consistency - e.g. strong consistency within a transactional system, eventual consistency to replicate out to an analytics system or third party. If an order is placed, might need strong consistency to get the order persisted, but then eventual consistency to sales analytics systems or a recommendation system that works based on historical orders.
* Caching is a good example of this
  * Caches are eventually consistent with the source data store, but we sacrifice some immediate update to get higher throughput at lower cost
* Can sometimes dial up or down consistency to trade off performance and availability (CAP theorem)
* Event driven architectures and microservices almost always require eventual consistency, since each individual system has its own independent data store 

TODO
https://docs.microsoft.com/en-us/azure/architecture/guide/design-principles/use-the-best-data-store
https://docs.microsoft.com/en-us/azure/architecture/microservices/design/data-considerations
https://docs.microsoft.com/en-us/azure/architecture/best-practices/caching#caching-and-eventual-consistency
https://en.wikipedia.org/wiki/CAP_theorem

Eventual consistency, loose coupling, and elasticity are all interrelated
* LC implies EC
* LC supports E

## Partitioning

Think about data stores - is everything really relational?
Sharding, partitioning, stamps
TODO scaling out usually cheaper than scaling up

? TODO
https://docs.microsoft.com/en-us/azure/architecture/guide/design-principles/partition
https://docs.microsoft.com/en-us/azure/architecture/best-practices/data-partitioning
https://docs.microsoft.com/en-us/azure/architecture/best-practices/data-partitioning-strategies


> **[prev]** | **[home]**  | **[next]**

[prev]:./requirements.md
[home]:/README.md
[next]:./cloud-design-patterns.md
[Knapsack problem]:https://en.wikipedia.org/wiki/Knapsack_problem
[Azure Well-Architected Framework - Maximize efficiency of cloud spend]:https://docs.microsoft.com/en-us/learn/modules/azure-well-architected-cost-optimization/5-maximize-efficiency-of-cloud-spend
[auto-scaling]: https://docs.microsoft.com/en-us/azure/architecture/best-practices/auto-scaling
[Azure Architecture Guide - Design to scale out]:https://docs.microsoft.com/en-us/azure/architecture/guide/design-principles/scale-out
[Application Architecture Guide - Minimize coordination]:https://docs.microsoft.com/en-us/azure/architecture/guide/design-principles/minimize-coordination
[Event-driven architecture style]:https://docs.microsoft.com/en-us/azure/architecture/guide/architecture-styles/event-driven
[Web-Queue-Worker architecture style]:https://docs.microsoft.com/en-us/azure/architecture/guide/architecture-styles/web-queue-worker
