# The Anatomy of a Release Pipeline

_Captured: 2017-04-04 at 22:39 from [dzone.com](https://dzone.com/articles/the-anatomy-of-a-release-pipeline?edition=288881&utm_source=Daily%20Digest&utm_medium=email&utm_campaign=dd%202017-04-04)_

The DevOps Zone is brought to you in partnership with Sonatype Nexus. The [Nexus Suite](https://dzone.com/go?i=146021&u=https%3A%2F%2Fwww.sonatype.com%2Fnexus-lifecycle%3Futm_source%3DDZONE%2520-%2520Nexus%2520Lifecycle%2520-%2520September%25202016%26utm_medium%3DDZONE%2520-%2520Nexus%2520Lifecycle%2520-%2520September%25202016%26utm_campaign%3DDZONE%2520-%2520Nexus%2520Lifecycle%2520-%2520September%25202016) helps scale your DevOps delivery with continuous component intelligence integrated into development tools, including Eclipse, IntelliJ, Jenkins, Bamboo, SonarQube and more. [Schedule a demo today](https://dzone.com/go?i=146021&u=https%3A%2F%2Fwww.sonatype.com%2Fnexus-lifecycle%3Futm_source%3DDZONE%2520-%2520Nexus%2520Lifecycle%2520-%2520September%25202016%26utm_medium%3DDZONE%2520-%2520Nexus%2520Lifecycle%2520-%2520September%25202016%26utm_campaign%3DDZONE%2520-%2520Nexus%2520Lifecycle%2520-%2520September%25202016).

Following my previous articles on DevOps, I've decided to write in more detail about the release pipeline. DevOps is a such a buzzword at the moment, but under the bonnet, what is actually involved?

In this article, I'll be dissecting release pipelines, which transform Continuous Deployment from an aspiration to a reality. I'll talk about the underlying building blocks that any good release pipeline will be comprised of and how they fit together.

## CI vs. CD

I think of Continuous Integration (CI) as being distinct and complimentary to Continuous Deployment (CD). I think of CI as a check on code quality and not of system quality. CI includes the following operations:

  * Static code analysis.
  * Semantic code analysis.
  * Compilation.
  * Code packaging.
  * Unit testing.

CI should run on every branch you push to measure and ensure quality throughout your entire codebase. CI should test every pull request before you merge into a protected branch. Successfully passing CI is a prerequisite for your code ever seeing the light of day.

Continuous Deployment is different. CD is the automated (or semi-automated) process by which committed code is released to production. CD is usually triggered by commits to a single branch (i.e., master) or a small subset of branches. You can safely commit new features into any old branch you like, safe in the knowledge that you're not going to put it live unless and until you then merge those commits into your CD branches. After that, you assume it's going live.

## Release Pipeline

The way we achieve this is to put into place a release pipeline. A release pipeline is a conceptual process by which we take committed code into production. As such, a release pipeline can be as ephemeral or as real as we want to make it.

![Basic Release Pipeline](https://cdn.345.systems/wp-content/uploads/2017/01/Basic-Release-Pipeline-1024x291.png)

> _The fundamental release pipeline from code change to production software._

There are some underlying capabilities we need in order to make sure we actually do have a release pipeline, though:

  * A means of triggering the pipeline to run.
  * A means of executing tasks such as environment provisioning, application deployment, testing, collation of test results.
  * A means of controlling the flow of execution, especially to stop further processing in the event of failure.
  * An artefact store to maintain state throughout the process.
  * A metadata store, allowing consistent metadata (such as build number) to be passed to each stage of the pipeline.
  * A configuration store, allowing environment-specific values to be retrieved for use in the pipeline.
  * Logging of the work performed and of any errors.
  * Notifications of success and failure.

A release pipeline can also be thought of as a workflow. A workflow whose purpose is releasing software. As such, modelling your release pipeline should simply be a case of modelling how you want to release your software.

## Triggers

Releases happen in response to one or more events. Often the triggering event is a code commit, but sometimes the release can be triggered manually or on a schedule.

You may also want your pipeline to run automatically up to a certain point (i.e., to the completion of pre-production testing), and then require manual approval to actually release into production. You may, therefore, want manual triggers to act as prerequisites for completion even though the start of the pipeline process is run automatically.

## Pipeline Stages

Pipeline stages are the control points in your release pipeline, and within a stage, you have tasks that are triggered. The key things to note about pipeline stages are:

  * A stage cannot start unless all of its prerequisites are fulfilled.
  * A stage cannot complete unless all of the tasks within it are complete.
  * Failures of any task (usually) result in the whole stage failing, and in turn, this usually fails the whole release.
![Basic release pipeline stages](https://cdn.345.systems/wp-content/uploads/2017/01/basic-pipeline-stages-1024x280.png)

> _Basic release pipeline stages, a sequential series of steps._

A simple pipeline like the one pictured above is a sequential series of stages. These types of release pipeline have usually descended from CI systems, where a build process is executed linearly from start to finish.

A more complex pipeline may use fan-out and fan-in, as a means of running stages in parallel and then collating the output from each. This can be an advantage in highly complex deployments where there are a series of services that need to be deployed and tested as part of the overall process.

![Parallel pipeline processing, fan out fan in.](https://cdn.345.systems/wp-content/uploads/2017/01/fan-out-fan-in-1024x420.png)

> _A pipeline supporting parallel processing via fan-out and fan-in._

The control of flow in your pipeline will vary depending on which model you use. In a simple pipeline, you can trigger the start of the next stage from the completion of the previous stage. In a fan-out/fan-in model, you need to find a way of allowing the stages to subscribe to their prerequisites. I'm not talking about underlying tech in this article, just what needs to happen.

## Repair and Restart

An optional feature in release pipelines is the ability to repair and restart. This can involve correcting environmental issues and then allowing failed tasks to start again and then hopefully resume the process.

Repair can work both ways, though. If you find that you're fixing machine settings then you really ought to be working on fixes to your infrastructure provisioning scripts instead of masking your underlying issues. If you've has a network blip then restart may be fair enough.

Not all release pipelines support repair and restart, and if yours does then use it wisely.

## Tasks

Tasks are the things that actually get done, at a granular level. Importantly, within a stage it should not matter which order the tasks complete in. Use stages as the gates in the control flow and tasks as the things that actually get done.

The tasks you will need include:

  * **Infrastructure provisioning**. This can include spinning up new virtual environments for test, or it can involve ensuring that a test environment is configured correctly and that the required services (i.e., web server) are installed and running.
  * **Application deployment**. This includes taking the packaged software and deploying onto the infrastructure instances, and making any environment-specific configuration changes as required.
  * **Testing**. Executing tests and publishing test results. You also need to be able to mark a stage as failed if the test run is not successful.
  * **Infrastructure shutdown**. After running a test phase any virtual infrastructure can be shut down or even decommissioned entirely to save costs.

Some tasks will be asynchronous, and your pipeline may need to be able to handle this. For example, an application that spins up AWS EC2 instances may have to wait a minute between the start of infrastructure provisioning and application deployment or testing while the environment is prepared.

## Artifact Store

In general, a release process starts with a code change and ends with provisioned infrastructure and deployed software. Along the way, the packaged software needs to be available for deployment to each environment and may need to be modified and/or configured for each environment. An artifact store, therefore, underpins the process.

![Release pipeline with artefact store](https://cdn.345.systems/wp-content/uploads/2017/01/artefact-store-1024x514.png)

> _A release pipeline with a supporting artifact store._

The artifact store also needs to support distinct artifact versions. The set of artifacts for a single build and release should be atomic and distinct from the artifacts from any other release with no cross-contamination.

Going back a few years we used to achieve this by having a network share for the build and release process, and each build having its own folder within that share. Whether you take this approach, whether you use a database, or even put everything into an S3 bucket, the persistence of artifacts is essential.

## Configuration Store

The artifact store contains different data (software) for each build and release. The configuration store contains values that are consistent between builds such as connection strings, API URLs, environment-specific users, and permissions.

![Release pipeline with a configuration store](https://cdn.345.systems/wp-content/uploads/2017/01/configuration-store-1024x718.png)

> _A release pipeline with a configuration store._

The configuration store will ultimately contain some of your production configuration, even if it's just machine names, so it is essential that your configuration store is secure and encrypted. Your release pipeline should be able to pull out the required configuration for any environment at the relevant stage of the pipeline and use it to allow you to provision and deploy.

## Logging

It goes without saying that if there are problems with your pipeline execution you need to be able to examine your logs to see where any problems occurred and what went wrong. In a system that has a lot of moving parts, you need to ensure that the logs are collated in such a way that you can make sense of them.

![A release pipeline with an added log store](https://cdn.345.systems/wp-content/uploads/2017/01/log-store-1024x693.png)

> _A release pipeline supported by a log store._

Everything you log will, therefore, need to be stamped with at least the following information:

  * Release pipeline/application.
  * Pipeline stage.
  * Build number.
  * Timestamp.

Beyond this, it's up to you how you visualize your logs. A very basic system might just collate them together and make them searchable, but sophisticated build pipeline software will give you a graphical view of the execution of your pipeline with drill-down into the logs.

## Metadata Store

The metadata store is one of the simplest features of the process. It is usually a collection of name-value pairs that contain build-specific information. Often these are exposed as environment variables, but depending on how you conceptualize your build data this could also be information on completion of stages and tasks.

![A release pipeline with a metadata store](https://cdn.345.systems/wp-content/uploads/2017/01/metadata-store-1024x664.png)

> _A release pipeline supported by a metadata store._

## Execution Engine

The release pipeline involves executing a workflow. How this actually works under the hood depends on implementation, but you need processes to execute. Whether this is a glorified bash script or a hosted workflow engine, somewhere the work actually needs to get done.

![](https://cdn.345.systems/wp-content/uploads/2017/01/execution-engine-1024x795.png)

> _A release pipeline powered by an execution engine._

## Notification Service

Notifications are optional but useful and almost universal. When your process succeeds or fails you generally want to tell someone about it, and usually that's via email. If you're in the modern SaaS webhook-y world (like 345) you might prefer to use a tool like [Slack ](https://slack.com/)for notifications. Whatever your preference, someone needs to know.

![A release pipeline with a notification service](https://cdn.345.systems/wp-content/uploads/2017/01/notifications-1024x809.png)

> _A release pipeline with a notification service._

## Process Viewer

Optional, but useful, is a graphical view of your pipeline. It's no coincidence that CD tools include some sort of graphical view because it's a truism of software that UI is the only thing people see of their software. UI is the tip of the iceberg, often the smallest part in terms of code and functionality but the only bit you can see.

![Release pipeline with process viewer](https://cdn.345.systems/wp-content/uploads/2017/01/monitor-1024x796.png)

> _A release pipeline with a graphical process view._

## Summary

So, that's the end of my tour of a release pipeline. I haven't talked about specific tools and technologies because I wanted to keep it at a conceptual level. I've highlighted the main features that allow the execution of your release process. Whether you're rolling your own release pipeline or using a package, you should be able to spot the same feature come up again and again. They may take different nomenclature depending on how the developers' vocabulary evolved and the paradigms they were using, but the essence will all be there.

The DevOps Zone is brought to you in partnership with Sonatype Nexus. Use the [Nexus Suite](https://dzone.com/go?i=146022&u=https%3A%2F%2Fwww.sonatype.com%2Fget-nexus-sonatype%3Futm_source%3DDZONE%2520-%2520Get%2520Nexus%2520-%2520September%25202016%26utm_medium%3DDZONE%2520-%2520Get%2520Nexus%2520-%2520September%25202016%26utm_campaign%3DDZONE%2520-%2520Get%2520Nexus%2520-%2520September%25202016) to automate your software supply chain and ensure you're using the highest quality open source components at every step of the development lifecycle. [Get Nexus today](https://dzone.com/go?i=146022&u=https%3A%2F%2Fwww.sonatype.com%2Fget-nexus-sonatype%3Futm_source%3DDZONE%2520-%2520Get%2520Nexus%2520-%2520September%25202016%26utm_medium%3DDZONE%2520-%2520Get%2520Nexus%2520-%2520September%25202016%26utm_campaign%3DDZONE%2520-%2520Get%2520Nexus%2520-%2520September%25202016).
