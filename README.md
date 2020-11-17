# FastTrack for Azure: Cloud architecture

This is the companion repo for the _Cloud architecture FastTrack for Azure: Live session_ run periodically by the Microsoft FastTrack for Azure team. This repo contains the presentation material and other assets for this session.

> For more information about the FastTrack for Azure team and FastTrack for Azure: Live sessions, visit [Azure.com/FastTrack].

This presentation is about architecture design in the cloud. This is important because the way we design solutions in the cloud has a large impact on things like scalability, cost, performance, security and management overhead. Making good architecture decisions during the design and requirements phase helps us to be more successful in the cloud and to have a better experience once we are in production.

## FastTrack for Azure: Live sessions

This presentation and content is written and delivered by Microsoft FastTrack for Azure engineers who work closely with customers in 1:1 engagements to design, configure and deploy solutions in Azure. Our customers' projects include some of the largest, most complex and critical workloads deployed into public cloud today. Our goal in a _FastTrack for Azure: Live_ session is to pass on generalized advice based on "real world" experience delivering thousands of engagements and hundreds of successful production deployments in Azure.

Hopefully the richness of our content will make up for our lack of presentation skills (we often don't use slides). Expect fast moving highly-technical content, strong opinions (held lightly) and honest views on the good, the bad, and the ugly.

> 📖 Visit [Microsoft FastTrack for Azure] to learn more about FastTrack.

## Goals of this session

By the end of this session we hope you will have a clear understanding of:

* What it means to be an architect of solutions in the cloud.
* How cloud architecture is different from traditional forms of architecture, and where it is the same.
* How engineers and architects can use the [Azure Architecture Center], the [Well-Architected Framework] and the [Cloud Adoption Framework] in their daily work, and how [Microsoft Learn] can help with learning about cloud architecture.

Our goal is that after this session, you will be able to explore the material on the [Azure Architecture Center], and to read the [Introduction to the Microsoft Azure Well-Architected Framework]. You will also be well prepared for architecture discussions and review sessions with FastTrack engineers.

> ℹ In this session we will focus on **Platform as a Service (PaaS)** services and architectural patterns. While there are many similarities with Infrastructure as a Service (IaaS) architectures, if you are only deploying IaaS services in cloud then not all examples may be relevant.  

## Who should attend?

Any engineer or architect who is involved in the design of cloud solutions and/or the formulation of cloud and technology strategy.

## What are the prerequisites?

We recommend you attend a *FastTrack for Azure Live: Governance* session before joining this session.

## Session outline

Today's session will run like this.

1. **Welcome, introductions**
   * About FastTrack for Azure
   * Other FastTrack for Azure: Live sessions
   * **[Azure Architecture Center](./docs/azure-architecture-center.md)**
     * Application architecture guide
     * Design patterns
     * Well-Architected Framework
     * Cloud Adoption Framework
1. **[Architecture in the cloud](./docs/cloud-architecture.md)**
   * The role of the architect
   * Architecture design session
   * Relative cost to fix
1. **[Cloud fundamentals](./docs/cloud-fundamentals.md)**
    * Cloud economics
    * Cloud models
    * Elasticity
    * Loose coupling
    * Eventual consistency
    * Partitioning
1. **[Reliability](./docs/reliability.md)**
    * Well-Architected Framework
    * High availability, Disaster recovery
    * Uptime, Recovery time objective, Recovery point objective
    * Azure SLAs
    * Architecture review
    * Resiliency patterns
1. **Final question time and wrap**

## Links

* [azure.com/FastTrack]
* [Azure Architecture Center]
* [Application Architecture Guide]
* [Cloud Adoption Framework]
* [Well-Architected Framework]
* [Microsoft Learn]
* [Build great solutions with the Microsoft Azure Well-Architected Framework] (Microsoft Learn)
* [LinkedIn Learning]
* [Pluralsight]

## Contributing

This project welcomes contributions and suggestions.  Most contributions require you to agree to a
Contributor License Agreement (CLA) declaring that you have the right to, and actually do, grant us
the rights to use your contribution. For details, visit https://cla.opensource.microsoft.com.

When you submit a pull request, a CLA bot will automatically determine whether you need to provide
a CLA and decorate the PR appropriately (e.g., status check, comment). Simply follow the instructions
provided by the bot. You will only need to do this once across all repos using our CLA.

This project has adopted the [Microsoft Open Source Code of Conduct](https://opensource.microsoft.com/codeofconduct/).
For more information see the [Code of Conduct FAQ](https://opensource.microsoft.com/codeofconduct/faq/) or
contact [opencode@microsoft.com](mailto:opencode@microsoft.com) with any additional questions or comments.

[azure.com/FastTrack]:https://azure.microsoft.com/en-us/programs/azure-fasttrack/
[Azure Architecture Center]:https://docs.microsoft.com/en-us/azure/architecture/
[Application Architecture Guide]:https://docs.microsoft.com/en-us/azure/architecture/guide/
[Cloud Adoption Framework]:https://docs.microsoft.com/en-us/azure/cloud-adoption-framework/
[Well-Architected Framework]:https://docs.microsoft.com/en-us/azure/architecture/framework/
[Microsoft Learn]:https://docs.microsoft.com/en-us/learn/roles/solutions-architect
[LinkedIn Learning]:https://www.linkedin.com/learning/search?keywords=Cloud%20Computing&u=3322
[Pluralsight]:https://www.pluralsight.com/browse/cloud-computing
[Build great solutions with the Microsoft Azure Well-Architected Framework]:https://docs.microsoft.com/en-us/learn/paths/azure-well-architected-framework/
[Introduction to the Microsoft Azure Well-Architected Framework]:https://docs.microsoft.com/en-us/learn/modules/azure-well-architected-introduction/
[Microsoft FastTrack for Azure]:https://azure.microsoft.com/en-us/programs/azure-fasttrack/