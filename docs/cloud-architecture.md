# Architecture in the cloud

> **[prev]** | **[home]**  | **[next]**

Solution architecture is concerned with the planning, design, implementation, and ongoing improvement of a technology system. The architecture of a system must balance and align the business requirements with the technical capabilities that are needed to execute those requirements. The finished architecture is a balance of risk, cost, and capability throughout the system and its components.

## The role of the Architect

A Solution Architect is someone who assists teams to design solutions that are fit for purpose. In the cloud this role is known as a "Cloud solution architect". In many teams Architect is a role, not a job title. It's important that every engineer learns cloud architecture patterns and practices.

## Do we need Architects in Agile?

While some teams have decided that having a dedicated Architect role is unnecessary, the need for good _architecture_ remains; in fact it is crucial for Agile teams that want to move fast, but still meet important business requirements around reliability, performance, operational excellence, cost and security. One approach for Agile teams is for all engineers to share the role of architect, putting on their "architect hat" from time to time. Another approach is to have an Architect available to the team as an _advisor_. Microsoft FastTrack for Azure engineers are often used in this capacity.

## Relative cost to fix and shift left

NIST conducted a study in 2002<sup>1</sup> observing that the relative cost to fix software defects increased exponentially the later they were discovered in the development process.

![Chart showing the relative cost to fix, based on time of detection](./images/relative-cost-to-fix.png) <br/>_Figure: Example of relative cost to fix, based on time of detection._

This research has been widely cited to _shift left_ testing processes from System / Acceptance Testing phase into Coding phase. However the impact from detecting defects in **Requirements / Architecture** phase are even more pronounced, with this example showing 30X saving in cost compared to detecting the same defect in Production / Post-Release.

## Azure Well-Architected Framework pillars

The Azure Well-Architected Framework consists of five pillars:

* Cost optimization
* Operational excellence
* Performance efficiency
* Reliability
* Security

> 📖 Read more in [Azure Well-Architected Framework pillars] (Microsoft Learn)

## Architecture design

Good practices in the design phase help to reduce issues in later phases of a system's life. While it is important to think about requirements in the early stage we should be careful not to fall into the trap of [Big Design Up Front] (BDUF); our design should evolve and continue to be refined until the end of the system's life. In the [reliability] section we will learn why business requirements are critical to good design, and can simplify the design process. This will be a recurring theme throughout this 1:many session.

An _architecture design session_ is a good way to kick-off a project. A small team of architects, engineers and product owners would meet to whiteboard a design, or to review a _candidate architecture_ that has already been researched and designed by a Solution architect. When critiquing a design the _vision_, _strategy_ and _business requirements_ should be kept firmly in mind. A _reference architecture_ may be used as a starting point.  

![Flow chart showing an example of an Architectural design process](./images/architecture-design-process-example.png) <br/>_Figure: Example of an Architectural design process._

> 💡 A Microsoft Cloud Solution Architect (CSA) is a good resource for the envisioning and design phase of a Cloud Architecture design in Azure. Contact your Microsoft Account Team to request assistance from a CSA.

Once a candidate architecture has been formed it should be documented in a diagram. An _architectural spike_ may be performed to validate assumptions. Detailed _research and design_ of each component should be undertaken. For example, it is vital that architects understand the limits of the services and components that are being used.

> 📖 [Azure subscription and service limits, quotas, and constraints]


## Architecture review

Once a candidate architecture has been formed and the team are getting close to starting Dev/Test, we recommend requesting an Architecture Review from the FastTrack for Azure team. In a 90 minute review session we will review your design to validate that it meets your business requirements and offer advice (including a list of recommendations and risks) where we see room for improvements. The goal of a FastTrack for Azure Architecture review is to help you be successful in your deployment to Azure and also to have a great experience once your are operating your system in production.

> 📖 [FastTrack for Azure Architectural / Solution Review and Guidance Framework]

## Roadmap

Migration and modernization projects are common in cloud. Rarely do systems go from current state to future state in one big bang. What is more common is a series of steps and milestones ([improvement kata]) on a roadmap towards deploying the future state architecture. We recommend breaking your project down into a series of milestones, each one delivering value to the business.

👷🏻‍♀️🚧👷🏻‍♂️ (WIP)

Combine with 👇🏻

## Note on existing systems
Often when moving an existing system from on-premises to the cloud (often refered to as application modernisation) There will be several constraints placed on the architecture because of the existing architecture. When this occurs you may not be able to follow all of the guidance discussed.

* often requirements are no longer known
* old protocols and architecture inflexible
* complex systems take time to change and will need a phased approach
* Phase 1 may simply involve substituting out components for similar PaaS services
* Investing in building api facades for legacy components to facilitate integration

## Azure SLAs

> 📖 Familiarize yourself with [Azure service-level agreements].

> 📺 Watch [SLIs, SLOs, SLAs, oh my!] for a definition of these terms and an explanation of the differences.

* An Azure Service-level Agreement (SLA) can also be read as a minimum service-level objective (SLO).
* An SLA is a financial guarantee, not an absolute guarantee
* Read the SLA details carefully, particularly the definition of "downtime" for each service, which give important hints about _failure modes_

For example, in the [SLA for Azure SQL Database], "downtime" is defined as:

_"The total accumulated Deployment Minutes across all Databases in a given Microsoft Azure subscription during which the Database is unavailable. A minute is considered unavailable for a given Database if **all continuous attempts by Customer to establish a connection to the Database** within the minute fail."_

The Azure SQL Database team expect almost all outages to be transient (brief and non-recurring). Therefore the _retry_ pattern should be used to continuously retry for up to a minute. This is typical in cloud services; retry has been the default behaviour in ADO.NET since .NET Framework 4.6.1.

## Links and references

1. [The Economic Impacts of Inadequate Infrastructure for Software] (PDF)

> **[prev]** | **[home]**  | **[next]**

[prev]:/azure-architecture-center.md
[home]:/README.md
[next]:./cloud-fundamentals.md
[Big Design Up Front]:https://en.wikipedia.org/wiki/Big_Design_Up_Front
[Azure Well-Architected Framework pillars]:https://docs.microsoft.com/en-us/learn/modules/azure-well-architected-introduction/2-pillars
[Azure subscription and service limits, quotas, and constraints]:https://docs.microsoft.com/en-us/azure/azure-resource-manager/management/azure-subscription-service-limits
[FastTrack for Azure Architectural / Solution Review and Guidance Framework]:https://github.com/Azure/fta-architecturalreview/blob/master/articles/introduction.md
[The Economic Impacts of Inadequate Infrastructure for Software]:https://www.nist.gov/system/files/documents/director/planning/report02-3.pdf
