# Operational excellence

> **[prev]** | **[home]**  | **[next]**

👷🏻‍♂️🚧👷🏻‍♀️ (WIP)

Operation Excellence underpins and is enabled by the other Pillars. That is it will be fundamental to your architectures success but also the difficulty and effort required to achieve excellence will depend on architecture choices. It will not directly influence your architecture in the same way as the other pillars but its important to consider the operational factors from the design phase.  Cloud architecture also needs to consider deploy and run state aspects of a system. These are often forgotten or ignored until later in a project and often results in refactoring and additional effort to compensate.
## DevOps
Devops is a key aspect of Operational excellence as it describes a common set of practices shared between developers and operations. These practices are critical for enabling shifting work left and enabling feedback loops.   
> 📖 For a list of the recommended practices see [Azure Well-Architected Framework - Operational Excellence].

* Key considerations
    * Is you architecture enabling good devops practices. 
    *  is your architecture being driven by your devops tool chain.
    * Availability : What happens if you source control is down or your deployment mechanism is unavailable
    * Complexity: ease of use, do you have the skills to operate, are they readily available in the market,
    

## Automation
* Automation is a critical factor of reliability
* Reliable and consitent deployments
* Remove possibility of human error
* You dont have to Automate everything from day 1 but it would be nice.
* Investing in automation upfront will be didends as the project progresses

## Monitoring & analytics
There is an overwhelming amount of telemetry available from cloud services. It can be hard to identify what signals are important and what the response should be. In addition your solution will have to emit its own telemetry, events and metrics. Trying to define your monitoring strategy at the end of the project is very time consuming and costly, so bake this in. There will often by multiple personas with different requirements when it comes to monitoring, including:
* Businesss: is the service online and fulfilling the business need, this may also extend into analytics like how users interact or what products are selling.
* Operations: Is the system healthy, do we need more or less resources is the configuration okay
* Developer: Is the code preforming, what needs to be optimized

Consider what a healthy system looks like and how that could be measured across the different components. Build in health reporting capabilities into each components so that it can easily be queried and aggregated. 
> 📖 Read more in [Azure Well-Architected Framework - Monitoring for DevOps].



> **[prev]** | **[home]**  | **[next]**

[prev]:./performance.md
[home]:/README.md
[next]:/README.md
[Azure Well-Architected Framework - Monitoring for DevOps]:https://docs.microsoft.com/en-us/azure/architecture/framework/devops/monitoring
[Azure Well-Architected Framework - Operational Excellence]:https://docs.microsoft.com/en-us/azure/architecture/framework/devops/overview