# Architecture in the cloud

> **[prev]** | **[home]**  | **[next]**

Solution architecture is concerned with the planning, design, implementation, and ongoing improvement of a technology system. The architecture of a system must balance and align the business requirements with the technical capabilities that are needed to execute those requirements. The finished architecture is a balance of risk, cost, and capability throughout the system and its components.

## The role of the Architect

A Solution Architect is someone who assists teams to design solutions that are fit for purpose. In the cloud this role is known as a "Cloud solution architect". In many teams Architect is a role, not a job title. It's important that every engineer puts their "Architect" hat on from time to time.

XXXXXXXXX Architecture role in Agile XXXXXXXXXXXXXX

## Azure Well-Architected Framework pillars

The Azure Well-Architected Framework consists of five pillars:

* Cost optimization
* Operational excellence
* Performance efficiency
* Reliability
* Security

> Read more in [Azure Well-Architected Framework pillars] (Microsoft Learn)

## Architecture design

Good practices in the design phase help to reduce issues in later phases of a system's life. While it is important to think about requirements in the early stage we should be careful not to fall into the trap of [Big Design Up Front] (BDUF); our design should evolve and the process should continue until the end of the system's life. In the next section we will learn why requirements are so important for design. This will be a recurring theme throughout this 1:many session.

An _architecture design session_ is a good way to kick-off a project. A small team of architects, engineers and product owners would meet to whiteboard a design, or to review a _candidate architecture_ that has already been researched and designed by a Solution architect. When critiquing a design the vision, strategy and business requirements should be kept firmly in mind. A _reference architecture_ may also be used as a starting point.  

> A Microsoft Cloud Solution Architect (CSA) is a good resource for the envisioning and design phase of a Cloud Architecture design in Azure. Contact your Microsoft Account Team to request assistance from a CSA.

Once a candidate architecture has been formed it should be documented in a diagram. An _architectural spike_ is used to validate assumptions and detailed _research and design_ of each component should be undertaken. For example, it is vital that architects have a good understanding of the limits of the services and components that they are using.

> Read: [Azure subscription and service limits, quotas, and constraints]

## Architecture review

Once a good candidate architecture has been formed and the team are getting close to starting Dev/Test then we highly recommend requesting an Architecture Review from the FastTrack for Azure team. In
a 90 minute review session we will review your design to validate that it meets your business requirements and offer advice (including a list of recommendations and risks) where we see room for improvements. The goal of a FastTrack for Azure Architecture review is to help you be successful in your deployment to Azure and also to have a great experience once your are operating your system in production.

> [FastTrack for Azure Architectural / Solution Review and Guidance Framework]

## Relative cost to fix




> **[prev]** | **[home]**  | **[next]**

[prev]:/README.md
[home]:/README.md
[next]:./requirements.md
[Big Design Up Front]:https://en.wikipedia.org/wiki/Big_Design_Up_Front
[Azure Well-Architected Framework pillars]:https://docs.microsoft.com/en-us/learn/modules/azure-well-architected-introduction/2-pillars
[Azure subscription and service limits, quotas, and constraints]:https://docs.microsoft.com/en-us/azure/azure-resource-manager/management/azure-subscription-service-limits
[FastTrack for Azure Architectural / Solution Review and Guidance Framework]:https://github.com/Azure/fta-architecturalreview/blob/master/articles/introduction.md