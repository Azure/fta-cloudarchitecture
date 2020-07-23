# Cloud fundamentals

Digital transformation has driven incredible demand for services and the servers that host them. The
cloud is essentially a solution to problems of economics and scale in server hosting. As a result of
the change in scale, we need to design and architect our systems a little differently so that we can
make the most of the infrastructure available.

The cloud has changed the way we think about architecting solutions. Cloud providers like Azure have
enormous pools of compute resources and storage, vast global networks, and handle a significant
amount of the administrative and management burden for you. There are a few principles you should
think about as you design your solution so that you can get the most out of being in the cloud.

> TODO: Copy some slides in here

* Traditional hosting model vs cloud
* Cloud computing models
* Relative costs
* IaaS -> Paas -> Serverless -> SaaS

## Economics of the cloud



## Cloud computing models


### Resiliency
Well-designed cloud architectures involve bringing together multiple components and external systems
into a single distributed system. But distributed systems are complex, and failures can propagate
through them. Cloud providers can ensure that your solution is highly resilient to failures if you
follow some key best practices.

Commodity hardware is what makes the cloud cheaper and easier to provision and work with, and this
means that failures are simply part of life. Most modern applications are expected to be available
24/7 and don't have the luxury of having maintenance windows. Instead of trying to avoid failures, a
good cloud architecture embraces the fact that failures happen and instead will recover from
failures gracefully. We plan for failures at every layer, and ensure we use techniques like the
Bulkhead, Retry and Circuit breaker patterns, queueing, decoupling components, and using Azure
regions and availability zones to provide geo-redundancy and disaster recovery capabilities.

Make sure that you keep the business requirements in mind, though. Deploying multiple instances of
a resource across regions might help to increase its resiliency and recoverability, but it may be
overkill for a small application that manages information with low importance.

### Flexibility and agility
Be prepared to rearchitect. Your requirements will change and evolve, and your user base or request
volumes will (hopefully!) increase as you grow. It often doesn't make sense to build a highly
scalable solution on day one of your business, so you will need to plan to rearchitect as you scale.
You will also want to take advantage of new technologies, services, and patterns. Traditional
enterprise solutions are treated as projects with a defined end date; in the cloud, you need to
allow for constant improvement.

### Elasticity
Cloud computing not only allows for high scale, it also allows for rapidly scaling your solution out
and in again. If you use this correctly, you can keep your costs low initially as you build out your
user base, while also rapidly responding to an influx of traffic or activity. To make the most of
the elasticity provided by the cloud it's generally best to prefer stateless applications where
possible, and to avoid having bottlenecks that might inhibit your ability to scale quickly.

### Loose coupling
Any non-trivial solution will be made up of multiple components that work together. The
communication and coupling between these components matters a great deal. Synchronous communication
might appear to be the simplest option initially, but any downstream delays or bottlenecks can cause
your entire solution's performance to be degraded. Loosely coupling your components, using
asynchronous communication, and making use of patterns like
[Queue-based load leveling](https://docs.microsoft.com/en-us/azure/architecture/patterns/queue-based-load-leveling)
and eventing can allow your components to scale independently of one another, and provide a buffer
between those components to protect them and increase the overall solution resiliency. If you want
to scale elastically, you really need to ensure your components are loosely coupled so that the
infrastructure can provision and deprovision workers dynamically.

### Automation
To get the most out of your cloud infrastructure, plan to automate your deployment and configuration
wherever possible. Make use of infrastructure as code approaches, scripting, and templating to
ensure that you can rapidly create new environments for both development and production scaling.
