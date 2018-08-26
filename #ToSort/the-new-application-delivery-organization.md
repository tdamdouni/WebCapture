# The New Application Delivery Organization

_Captured: 2018-04-11 at 20:28 from [dzone.com](https://dzone.com/articles/the-new-application-delivery-organization?edition=373194&utm_source=Zone%20Newsletter&utm_medium=email&utm_campaign=microservices%202018-04-11)_

Containerized Microservices require new monitoring. See why a new APM approach is needed to even [see containerized applications](https://dzone.com/go?i=279427&u=https%3A%2F%2Fwww.instana.com%2Flibrary%2Febook-application-monitoring-in-containerized-world%2F%3Futm_source%3DdZone%26utm_medium%3Dpre_post_article_text_ad%26utm_campaign%3Dcontainer_apm_ebook%26utm_content%3Deverything_changed).

Changing IT delivery processes, technologies and philosophies are pushing traditional IT organizational structures the way of the dinosaur. Over the past few years, there has been a notable shift in how organizations develop, deploy, and manage applications. The analysis contained within this post is based upon our experience working with countless organizations ranging from SMB to large enterprise over the past 6 years.

## Old School Application Delivery

The traditional IT delivery organization is segregated between operations, development, and the business. Main functions of Ops included infrastructure design and deploy, perf test, integration test, application deployment, and the many tasks associated with supporting production (patching, version alignment, hardware refresh, incident triage, etc.). The operations group has a full workload trying to achieve 3 to 5 nines of infrastructure uptime.

![](https://www.instana.com/media/traditional-application-delivery.png)

Then there's the application development group who needs to design and build the actual apps themselves. They rarely interact with the operations team but they are regularly pushing code over the wall so that ops can get it deployed into production. It's ops job to get the apps configured and sized properly in production.

And the business typically has little to no interaction at all with operations but they communicate with the app dev organization to provide the business requirement that the developers will code to.

The communication between these silos is relatively infrequent and minimal in nature. This is the way IT organizations have operated for 20+ years. But then a few years ago something happened that started to change this very structured and siloed delivery methodology.

## There's a Better Way

New software delivery and management processes arose out of the need to deliver faster with higher quality. Agile replaced waterfall, developers became responsible for the performance and stability of their code in production, operations and developers started codifying infrastructure deployment, and continuous integration and continuous deployment tools arrived on the scene to enable automatic code testing and deployment.

At the same time, new architectural tools and patterns have developed a high level of maturity and adoption. Public and private cloud computing have become common in even the slowest moving large enterprises while container adoption and microservices architectures are dominating the discussions for new or re-architected applications.

All of these factors have created a seismic shift away from traditional delivery organizations to a new application delivery model.

![](https://www.instana.com/media/new-application-delivery.png)

This new model is built on a foundation of platform infrastructure components that can be used by service developers at will. The [platform engineering team ](https://www.instana.com/apm-platform-engineering/)no longer needs to manage server refreshes, operating system upgrades, or any of the time wasting tasks of the past. Now they ensure that the platform components are properly sized, configured, and available to the services that run on them.

The services layer is managed by developers who select whatever language is best to achieve the business goal. These [developers create API driven microservices](https://www.instana.com/apm-service-development/) that can be used by applications to achieve a business outcome. There are usually 10's or 100's of thousands of these microservices that developers are actively managing in production to ensure proper service performance and stability.

The final layer consists of business process and application veneers that create the proper user functions out of the myriad of available microservices. This is where you have a combination of [business analysts, front end, and app developers, as well as the fairly new role of SRE](https://www.instana.com/apm-service-development/) who take a holistic approach to ensuring quality customer experiences from this delivery methodology.

These layers are not individual teams. Instead, cross-functional teams are formed that can either be permanent or transient, working together for only weeks or months before moving on to their next project.

The new application delivery organization generates delivery speed with a better overall customer experience due to the fluid yet highly integrated nature of these cross-functional teams.

The last consideration with this new application delivery organization is whether or not to create a centralized monitoring service. It has become well understood that when you release new application code so frequently you must be able to observe the impact of those releases so that you can quickly roll back if there is a major unintended bad CX. There are many organizations that select, build and operate their monitoring platforms within a centralized team but the converse is also true. A fair number of organizations have left monitoring platform decisions to members spread across platform, services and application layers.

## Out With the Old, In With the New - Not So Fast!

The reality for most companies today lies somewhere between the traditional IT delivery organization and the new application delivery organization. Changing the way people organize to accomplish their work is more challenging than adopting new architectures and technologies. Many companies are in the midst of a transition with some portion of the traditional delivery organization and some other portion running something similar to the new application delivery organization.

## With Great Agility Comes Great Responsibility

One thing that has become evident with the transition to the new application delivery organization is that the need for observability will continue to grow. With rapid change and frequent releases, you MUST have visibility and understanding of the health and performance of every component and service involved in the delivery of your business. In many cases, the applications are so complex that Artificial Intelligence is required to achieve the requisite understanding. To do anything less is irresponsible and creates a perfect environment for frequent large-scale outages. Here are some of the key elements to consider for your observability solution:

  * Automatic 
    * Install easily with as little configuration as possible
    * Discover and monitor everything that's important without human interaction
    * Detect and analyze every infrastructure change and code deployment as they happen
  * Fast 
    * Stream metric and trace data in real-time, keep data lag as minimal as you can
    * 1-second granularity is the new standard for metrics, 10 second or longer averages are not granular enough for dynamic applications
    * Detect and alert on problems within a few seconds, 5-10 minute lag times on alerts burn up revenue quickly
  * Smart 
    * Use AI to determine root cause of application issues
    * Codify expert knowledge to make recommendations or automatically fix problems
    * Correlate and link the results of your observability solution directly to your running application code - make life easy for your developers and save resolution time

The new application delivery organization is a key enabler to delivering application features and fixes faster with higher quality. The transition from traditional application delivery and IT operations will pay dividends as long as you implement observability solutions as a foundational tenet along your journey. At [Instana](https://www.instana.com/), AI-powered APM is the cornerstone of responsibly implementing the principles of modern application delivery and management. Learn more about Instana's [AI-Powered APM solution ](https://instana.com/application-management)and see for yourself.

Got Cloud? Containers? Microservices? Get better control and performance. [Start your trial ](https://dzone.com/go?i=279428&u=https%3A%2F%2Fwww.instana.com%2Ftrial%3Futm_source%3DdZone%26utm_medium%3Dpre_post_article_text_ad%26utm_campaign%3Dinstana_trial%26utm_content%3Dgot_cloud_get_instana)of Instana APM today.
