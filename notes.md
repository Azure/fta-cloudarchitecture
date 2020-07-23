# Odds and ends
For inclusion in sections if they are helpful - ignore if not

## Cloud computing models
IaaS, PaaS, serverless, SaaS

## Flexibility and agility
Be prepared to rearchitect. Your requirements will change and evolve, and your user base or request
volumes will (hopefully!) increase as you grow. It often doesn't make sense to build a highly
scalable solution on day one of your business, so you will need to plan to rearchitect as you scale.
You will also want to take advantage of new technologies, services, and patterns. Traditional
enterprise solutions are treated as projects with a defined end date; in the cloud, you need to
allow for constant improvement.

## Resiliency
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

## Automation
To get the most out of your cloud infrastructure, plan to automate your deployment and configuration
wherever possible. Make use of infrastructure as code approaches, scripting, and templating to
ensure that you can rapidly create new environments for both development and production scaling.
