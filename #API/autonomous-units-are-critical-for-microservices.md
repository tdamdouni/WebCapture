# Autonomous Units Are Critical for Microservices

_Captured: 2018-06-06 at 21:37 from [dzone.com](https://dzone.com/articles/autonomous-units-are-critical-for-microservices?edition=376267&utm_source=Zone%20Newsletter&utm_medium=email&utm_campaign=microservices%202018-05-09)_

Containerized Microservices require new monitoring. See why a new APM approach is needed to even [see containerized applications](https://dzone.com/go?i=279427&u=https%3A%2F%2Fwww.instana.com%2Flibrary%2Febook-application-monitoring-in-containerized-world%2F%3Futm_source%3DdZone%26utm_medium%3Dpre_post_article_text_ad%26utm_campaign%3Dcontainer_apm_ebook%26utm_content%3Deverything_changed).

Microservices provide a historical improvement in the way we design, build and manage IT assets. It's probably the most important change in IT in the last 10-20 years. After helping a number of customers with microservices, we see how they make a huge difference in productivity, improving the optimism within the teams that build them: " _Autonomous teams owning autonomous components, using a [high productivity platform](https://www.mendix.com/resources/gartner-high-productivity-apaas/)."_ There's probably no more productive combination than that

Automation in infrastructure, deployments, and operations has reached a level where there is only a small operational cost in having more components. This is thanks to e.g. cloud, CI/CD and hpaPaaS solutions like Mendix. It means that focus for architects and developers can become more functional and IT components can be designed as autonomous business components.

## **Autonomous Units**

Designing autonomous units is something architects are still struggling with today. Maybe it goes against fundamental principles we were taught about re-use, normalization, and de-duplication. But these are man-made rules, and it's interesting to see what we learn from nature:

![](https://images.mendix.com/wp-content/uploads/Blog-inpost-architecture-series02.png)

Ants, dogs, elephants, and humans all have a head, a body, legs, and feet and/or hands, allowing individuals to operate autonomously. In several cases, groups of individuals work together for a purpose. This is not by accident. These species survived ages of evolutionary competition to still be viable in today's world.

In nature, nobody puts all the heads together in one place. Nobody suggests collecting all the legs of these organisms into one package to 'specialize' on that technical capacity. They would produce nothing. It would never work.

In nature, different species, and individuals within the species specialize in certain functional roles that improve the livelihood of groups and individuals. Copying is common for ultimate efficiency. On the contrary, in IT, the unrestrained desire to re-use things has tied the legs together of many good projects, increasing dependencies, and limiting flexibility and speed.

![](https://images.mendix.com/wp-content/uploads/Blog-inpost-architecture-series03.png)

## **Sharing Knowledge**

In the real world, we endorse copying of data every day. Students and co-workers become a lot more efficient when they acquire new skills and learn facts. Copying some data helps them retain knowledge and do what they need to do more efficiently. All schools or workplaces prepare Autonomous Units to live, work, eat, see, run, observe, and invent. To do this, we must copy some functions and some information over. Only the required information in the context of what is needed for a business function is copied, so it is rarely a complete replication.

![](https://images.mendix.com/wp-content/uploads/Blog-inpost-architecture-series04-copy.png)

Nobody suggests re-using knowledge in real-time by running to the expert every time you need a piece of knowledge. No one suggests that we can eliminate going to school because the students could just call the teacher when they need the information. It simply doesn't work and the results would be a slow, co-dependent society. Even the common phrase ' _just Google it_ ' doesn't remove the need for school. As teachers share functions, knowledge, and data with students, they merge the information with their own thinking and background, and new valuable combinations occur.

And yet, too often, we suggest retrieving data in real-time to avoid duplication. In the future, there will be no simple silver-bullets. There may be good reasons to avoid duplication within a single microservice, but if we do not duplicate data and functions between different microservices, the result will be a distributed system with all the problems and dependencies seen in SOA layers and Monoliths.

The innovation is in the combination as much as in the base science and knowledge. In the era of Robotics, let's start in IT by making the IT components as autonomous as possible, and take it from there. Infrastructure is now the commodity and Business Function is the area of innovation.

## **Looking Forward**

Organizations that want to get [DevOps](https://www.mendix.com/devops/) and microservices right, need to unlearn the habit of ambitious re-use in favor of creating new and awesome combinations. Call them apps, microservices or MSA systems, it does not matter, just make them autonomous and business oriented.

We are moving into the era of DevOps, Microservices, and Robotics:

  1. We should make IT components as functional and autonomous as possible. This often means having GUI, data, workflow, and logic in the same design module and deployed as one container.
  2. It makes sense to buy the right level of microservices delivery Automation. A good hpaPaaS removes all mundane tasks of IT delivery, accelerates production, improves quality and reduces risk

Cloud native platforms have scaling, resilience, automation, and monitoring in the package. If you choose a package that does not have this, you risk spending a large portion of time with very techie developers trying to build an automation pipeline that in the end still is less efficient than the native version.

The CICD and Auto-test pipelines will be hard (or impossible) for functionally oriented DevOps teams to manage and keep up to date, losing the essential part where the DevOps can automate its own processes and stay in control of deployments.

Similarly, be very careful with making too small and technical microservices that share databases. It removes the benefit of Business & IT alignment, and the microservices are not truly autonomous. The next blog will cover this important subject.

This article was originally published on the [Mendix blog](https://www.mendix.com/blogs/).

[Automatically manage containers and microservices](https://dzone.com/go?i=290421&u=https%3A%2F%2Fwww.instana.com%2Ftrial%3Futm_source%3DdZone%26utm_medium%3Dpre_post_article_text_ad%26utm_campaign%3Dinstana_trial%26utm_content%3Dgot_cloud_get_instana) with better control and performance using [Instana APM](https://dzone.com/go?i=290421&u=https%3A%2F%2Fwww.instana.com%2Ftrial%3Futm_source%3DdZone%26utm_medium%3Dpre_post_article_text_ad%26utm_campaign%3Dinstana_trial%26utm_content%3Dgot_cloud_get_instana). Try it for yourself [today](https://dzone.com/go?i=290421&u=https%3A%2F%2Fwww.instana.com%2Ftrial%3Futm_source%3DdZone%26utm_medium%3Dpre_post_article_text_ad%26utm_campaign%3Dinstana_trial%26utm_content%3Dgot_cloud_get_instana).
