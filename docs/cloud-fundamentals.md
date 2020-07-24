# Cloud fundamentals

> **[prev]** | **[home]**  | **[next]**

Digital transformation has driven incredible demand for services and the servers that host them. The
cloud is essentially a solution to problems of economics and scale in server hosting. As a result of
the change in scale, we need to design and architect our systems a little differently so that we can
make the most of the infrastructure available.

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

Virtualisation helped to get a bit more efficient use of our infrastructure, since we could
provision capacity and spread it across multiple workloads. But for most companies it was
challenging to achieve optimal density of VMs to hosts due to the
[knapsack problem](https://en.wikipedia.org/wiki/Knapsack_problem). Scaling VMs up often requires
even more infrastructure to be provisioned.

The cloud is essentially a hyperscale virtualisation environment. Cloud regions (comprised of
multiple datacentres) can host millions of cores and petabytes of RAM and storage. As there are so
many resources available, the law of large numbers dictates that the we can achieve better density
and can generally have a much better chance of fulfilling scale requests. The economies of scale
also mean that the average marginal cost (of additional CPU/RAM/storage) can often be much lower in
the cloud.

### Relative cost of resources

TODO

![Relative cost of resources](./images/relative-costs.png)

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

![Relative cost of resources](./images/cloud-computing-patterns.png)

Each of these take advantage of **elasticity** - the large pool of resources means that new
resources can be rapidly provisioned when they are required, used for as long as they are needed,
and then deprovisioned.

By taking advantage of elasticity you can keep your costs low initially as you build out your
user base, while also rapidly responding to an influx of traffic or activity.

To make the most of the elasticity provided by the cloud there are a few things you can do such as:
* Prefer stateless applications wherever possible, so that you can rapidly shift your traffic
  around and don't have to pin specific requests to specific compute instances.
* Avoid having bottlenecks that might inhibit your ability to scale out quickly.
* Loosely couple your components so that you can scale each part of your solution independently.

## Loose coupling
Any non-trivial solution will be made up of multiple components that work together. The
communication and coupling between these components matters a great deal.

Synchronous communication is often the simplest approach to implement. It also is typically more
performant, since messages are sent directly from point to point. This can be a good approach for
simpler systems, or for communicating between two parts of a solution that are highly
interdependent - for example, talking from an application to a database or cache.

However, in some situations tight coupling will lead to problems. Any downstream delays, failures,
or bottlenecks can cause your entire solution's performance to be degraded. Tightly coupling
components together also means you often can't easily take advantage of horizontal scaling.

Loose coupling, on the other hand, requires asynchronous communication. It often involves 
message brokers like Service Bus. Instead of sending requests directly between systems, the sender
instead send a message to a broker, and the destination system subscribes to the broker and
receive its instructions on what to do. Alternatively, eventing can be used for components to 
publish information about actions that have taken place into a central broker, and other components
can listen to the events coming from that broker events and decide when they might need to take
action. 

Loose coupling has some important benefits for resiliency and elasticity.
* **Resiliency:** loose coupling means there is a buffer between your solution components to
  protect them one another's failures. This typically increases the resiliency of the overall solution.
* **Elasticity:** to achieve elastic scale, it helps to have loosely coupled components. Adding
  additional compute workers and removing unnecessary compute workers can be achieved without
  upstream systems needing to be aware of the scaling.

## Eventual consistency

TODO

> **[prev]** | **[home]**  | **[next]**

[prev]:./requirements.md
[home]:/README.md
[next]:./cloud-design-patterns.md
