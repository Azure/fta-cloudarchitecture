# FastTrack for Azure: Well-Architected

This is the companion repo for the _Well-Architected 1:many session_ run periodically by the FastTrack for Azure team. This repo contains the presentation material and other assets for this 90 minute session.

> For more information about the FastTrack for Azure team and 1:many sessions, visit [Azure.com/FastTrack].

This presentation is about Architecture design in the Cloud. This is important because the way we design solutions in the cloud has a large impact on things like scalability, cost, performance, security and management overhead. Making good architecture decisions during the design and requirements phase helps us to be more successful in Cloud and to have a better experience once we are in Production.

## 1:many sessions

This presentation and content is written and delivered by FastTrack for Azure engineers who work closely with customers in 1:1 engagements to design, configure and deploy solutions in Azure. Our customers' projects include some of the largest, most complex and most critical workloads deployed into Public Cloud today. Our goal in a _1:many_ session is to pass on generalized advice based on "real world" experience delivering thousands of engagements and hundreds of successful production deployments in Azure.

Hopefully the richness of our content will make up for our lack of presentation skills (we often don't use slides). Expect fast moving highly-technical content, strong opinions (held lightly) and honest views on the good, the bad, the ugly.

> 📖 Visit **[Microsoft FastTrack for Azure]** to learn more about FastTrack

## Azure Well-Architected Framework

FastTrack for Azure team are contributors to the [Azure Architecture Center] which contains several excellent resources for Architects including [Application Architecture Guide], [Cloud Adoption Framework] and [Well-Architected Framework]. All of the architecture advice given by FastTrack in 1:1 or 1:many sessions is backed by the patterns and practices in these guides. In this presentation we will focus on the [Well-Architected Framework] (although we recommend you study them all).

## Goals of this session

By the end of this session we hope you will have a clear understanding of:

* What it means to be an architect of solutions in the cloud
* How cloud architecture is different from traditional forms of architecture, and where it is the same
* To demonstrate how engineers and architects can use the [Azure Architecture Center], the [Well-Architected
  Framework] and the [Cloud Adoption Framework] in their daily work
* To familiarise Engineers and Architects with training resources like [Microsoft Learn]

## Who Should Attend?

Any engineer or architect who is involved in the design of cloud solutions and/or the formulation of cloud and technology strategy.

## What are the prerequisites?

* Complete the [Introduction to the Microsoft Azure Well-Architected Framework] module in Microsoft
  Learn
* Familiarize yourself with the [Azure Architecture Center]
* Consider guided learning paths like [Microsoft Learn], [LinkedIn Learning] and [Pluralsight]

## Session Outline

This 90 minute 1:many session we will run like this. Each top-level section will run for about 10 minutes.

1. **Welcome, introductions**
   * About FastTrack for Azure
   * Other 1:many sessions
   * Azure Architecture Center and the Well-Architected Framework
1. **[Architecture in the cloud](./docs/cloud-architecture.md)**
   * The role of the Architect
   * Architecture design session
   * Architecture review session
   * Relative cost to fix
1. **[Well Architected Framework]**
1. **[Cloud fundamentals](./docs/cloud-fundamentals.md)**
    * (Cloud economics)
    * Elasticity
    * Loose coupling
    * Eventual consistency
    * **[Cloud design patterns](./docs/cloud-design-patterns.md)**
1. **[Reliability](./docs/reliability.md)**
    * Well architected framework
    * Shared responsibility
    * HA, BC/DR
    * Uptime, RTO, RPO
    * Azure SLAs
    * Architecture review
    * Resiliency patterns
1. **Final question time and wrap**


<!-- 
1. **[Requirements, requirements, requirements](./docs/requirements.md)**
    * Bringing business requirements to the design process
    * Service selection
    * Requirements mapping to features
    * What's important to various Personas
    * What about security?
-->
<!-- 1. **[Performance & cost optimisation](./docs/performance.md)** -->
<!-- 1. **[Operational excellence](./docs/ops.md)** -->

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