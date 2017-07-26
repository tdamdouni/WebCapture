# Forget DevOps; Let’s Do OpsDev 

_Captured: 2017-01-14 at 20:09 from [dzone.com](https://dzone.com/articles/forget-devops-lets-do-opsdev?edition=263881&utm_source=Daily%20Digest&utm_medium=email&utm_campaign=dd%202017-01-14)_

[Discover how to optimize your DevOps workflows](https://dzone.com/go?i=161129&u=http%3A%2F%2Finfo.saucelabs.com%2Fpaper-the-devops-journey.html%3Futm_campaign%3Ddevopsjourney%2Bwp%26utm_medium%3Dtextlink%26utm_source%3Ddzone-devops%26utm_content%3Darticle) with our cloud-based automated testing infrastructure, brought to you in partnership with [Sauce Labs](https://dzone.com/go?i=161129&u=http%3A%2F%2Finfo.saucelabs.com%2Fpaper-the-devops-journey.html%3Futm_campaign%3Ddevopsjourney%2Bwp%26utm_medium%3Dtextlink%26utm_source%3Ddzone-devops%26utm_content%3Darticle).

Much (and we mean much, a lot, really loads in fact) has been written about that most famous technology portmanteau of all DevOps as the coming together of Developer concerns with the Operations functions from sysadmins to DBAs and onward that support our programmers. However, should DevOps have really been called OpsDev to embody the foundational architectural needs of our systems in the first instance?

## Implications of Application Interconnectivity

Going forward, companies will attempt to capitalize on offering an integrated and personalized digital user experience, where several online services will be integrated to create a seemingly unified always-on customer experience across multiple channels and user touch-points.

This means a customer's experience with a brand or company will span many interconnected applications, all comprised of different code bases, data sources, hosted at the different data centers, designed and developed by different teams, using different technologies and APIs, and so on.

## The Operations Responsibility

From an operations standpoint, while the applications and code might be separated, in this always-connected world, there's a need to ensure all the components of the service are always running smoothly and that no service interruptions occur. Clearly, the delivery of inter-connected and personalized software applications has an impact on application design, development, and operations paradigms.

DevOps has emerged to help companies be better and delivering software to their end users. DevOps practices have traditionally originated on the Development side of software delivery, as they first emerged to address developer-led challenges with practices such as Agile development, code review, and code standards, build automation and continuous integration, and more.

Ultimately, DevOps spans the spectrum of the entire software delivery pipeline from Dev to Ops, and its true value (and biggest ROI) is ultimately in the Operations side once the application is promoted into Production and the value is actually being delivered to end users.

In that sense, we can coin a new term -- OpsDev - which begins with that end in mind.

## OpsDev Means Front-Loading Ops Considerations Early

In addition, the automation of the delivery pipeline itself -- including all the toolchain, processes, tests, etc. -- that ushers code from the CI stages all the way through to deploying into Production is being designed and developed in parallel to designing the product.

The pipeline itself is a critical component of the application and not an afterthought. This ensures fidelity of artifacts and configurations across all the environments throughout the software delivery process, better quality product, fewer errors caused by manual tasks, accelerated delivery, and streamlined operations in Production.

## Remember: First Pants, Then Shoes

For example, the dependencies of the various application components must be understood and modeled before the software development process begins.

  * The consideration for infrastructure stability, environment modeling, security, and audit and compliance measures are first and foremost. Application components are stubs and they do not need to be in their final forms.
  * The environments in which the components will be deployed for production must be modeled.
  * The processes to deploy the various components to the target environments must be automated as much as possible.

By doing the above, the design and development teams can replicate the application and environment models and automated processes in the development and test phases in a consistent and repeatable way.

By easily replicating the production environment and processes in development and test phases, the independent design, development, and testing teams will know the production constraints and parameters very early on, such that they develop the applications with those constraints and parameters in mind. OpsDev ensures more predictability and reliable operations.

Whereas, in the traditional model of application delivery, often a lot of time is wasted troubleshooting applications that have been approved by QA in the Staging or Production data centers but do not run well in Production. Often times, the release to end users must be significantly delayed because the applications are dead on arrival once deployed in Production, due to configuration drifts, etc.

## Release Pipeline

In the OpsDev approach, a Release pipeline that orchestrates the deployment of applications to dev, test, staging, and Production environments not only accelerates the overall process of deployments in various environments through automation and parallelization but it also improves quality by minimizing error-prone manual tasks. The Release pipeline aggregates several Commit pipelines that make up a Release. A commit pipeline is the individual CI or feature and component pipeline and a Release may contain several application components developed by several teams.

The Release pipeline has to understand the interdependencies among the application components and marshal those into Staging and Production environments. The Release pipeline can have manual and automatic approval gates to make sure that the Release is approved and is going in the right deployment schedule.

## ITSM Integration

From the OpsDev approach, the Release pipeline can be integrated with ITSM (Information Technology Service Management) and APM (application performance monitoring) solutions. The pipeline can report back to those tools to ask for an approval to an automated task, record a task as completed as code is promoted through the different stages in the pipeline, or these tools can trigger certain next steps that are automated by the Pipeline orchestration.

Similarly to integration with service desk tools, the Release pipeline can also kick off the APM solution to monitor the performance and load testing once an application has been deployed, or perform automatic tasks - such as scaling or auto failover - upon receiving certain signals from the monitoring tools.

## Final Thoughts

The proliferation of software in every aspect of our connected lives and the role software applications play in the user-experience of today's consumers all make mastering the way we deliver and manage software updates critical to the success of businesses today. Because of the increased interdependencies between these digital services and application components (SaaS, software in devices, software in data center, mobile apps, web app, and more), we need to encourage developers to think Ops-first, to accelerate the mind shift from DevOps to OpsDev.

Remember, you could have developed the most amazing killer-feature, but what good does it do you or your customers if it then takes you months to see it through to Production and have it run reliably? OpsDev is real.

[Download "The DevOps Journey - From Waterfall to Continuous Delivery"](https://dzone.com/go?i=161130&u=http%3A%2F%2Finfo.saucelabs.com%2Fpaper-the-devops-journey.html%3Futm_campaign%3Ddevopsjourney%2Bwp%26utm_medium%3Dtextlink%26utm_source%3Ddzone-devops%26utm_content%3Darticle) to learn learn about the importance of integrating automated testing into the DevOps workflow, brought to you in partnership with [Sauce Labs](https://dzone.com/go?i=161130&u=http%3A%2F%2Finfo.saucelabs.com%2Fpaper-the-devops-journey.html%3Futm_campaign%3Ddevopsjourney%2Bwp%26utm_medium%3Dtextlink%26utm_source%3Ddzone-devops%26utm_content%3Darticle).
