# Docker and Continuous Delivery Deployment Types

_Captured: 2018-01-12 at 20:11 from [dzone.com](https://dzone.com/articles/docker-amp-continuous-delivery-deployment-types?edition=352108&utm_source=Zone%20Newsletter&utm_medium=email&utm_campaign=devops%202018-01-12)_

In response to accelerated release cycles, a new set of testing capabilities is now required to deliver quality at speed. This is why there is a shake-up in the testing tools landscape--and a new leader has emerged in the just released [Gartner Magic Quadrant for Software Test Automation](https://dzone.com/go?i=265440&u=https%3A%2F%2Fwww.tricentis.com%2Fresource-assets%2Fgartner-magic-quadrant-software-test-automation%2F%3Futm_source%3DDZone_Pre_Roll%26utm_medium%3DText_Ads%26utm_campaign%3DDZoneDevOps%26utm_content%3D2017GartnerMQ).

In the companion piece to this blog post--[A 5-Step Guide to Good Continuous Delivery](http://caylent.com/a-5-step-guide-to-good-continuous-delivery)--we looked at the best practices high-performing IT teams should be employing to achieve Continuous Delivery (CD) with Docker. CD is achievable using numerous deployment methods and Docker is just one tool to help realize the necessary customizable "workflow-based" integration/build process.

## Continuous Delivery Deployment Types

Now, we're going to examine the four major deployment types and outline each of their advantages and disadvantages. These are:

  * Minimum In-Service deployment
  * Rolling application updates
  * Blue/Green deployment
  * A/B testing

These four deployment types fall into two sub-categories: application and infrastructure deployment.

### Minimum In-Service Deployments

With this method, we specify the minimum number of instances in our applications that stay in-service while updating the remaining percentage--therefore, deploying to as large a number of targets as possible. This process is repeated until all servers have been updated with the new release.

**Example:** If we have 5 containers each running our current application A, then we set our policy to keep a minimum in-service number of 2. We take 3 servers offline to update them to our new version B. Once these are completed and back online, we can update the remaining 2.

![Continuous Delivery Deployment Types: Minimum In-Service Deployments](https://i1.wp.com/caylent.com/wp-content/uploads/2017/10/min-in-service.png?w=1183&ssl=1)

#### Disadvantages

  * The process happens in multiple stages, so support is necessary in the form of orchestration and health checks outside of Swarm
  * Does not work well for infrastructure changes
  * Changes are being run on live servers--recovery time may be necessary if one fails

#### Advantages

  * There are few moving parts, which means increased testing capability; make application and code changes within the process
  * No downtime and no additional infrastructure cost
  * The process is often quicker than a rolling deployment (see below)

### Rolling Deployments

Consider rolling deployments as an extension of minimum in-service. However, rather than define the number of containers that should remain online, we specify the maximum number of containers to update in tandem.

**Example:** We have the same 5 containers as before, but this time we initialize rolling updates by specifying the number of containers that may be updated simultaneously, e.g. 2. The process moves updates through 2 containers at a time until all the servers in the series are updated.

Note: Docker Swarm supports rolling updates out the box; the default is to update one container at a time. To modify this use the _-update-parallelism setting_

![Continuous Delivery Deployment Types: Rolling Deployments](https://i1.wp.com/caylent.com/wp-content/uploads/2017/10/Rolling-Deployments.png?w=941&ssl=1)

#### Disadvantages

  * Docker rolling updates deal with failure in two ways: 
    * By pausing, allowing someone to jump in and rollback to fix
    * Or continuing regardless, meaning you may not discover a problem while the container is running
  * More complex than minimum in-service
  * Can be the least efficient in terms of deployment time; based on the time taken to update per stage
  * Again, we recommend orchestration and health checks outside of Swarm

#### Advantages

  * No downtime
  * Pausing is possible, permitting limited multi-version testing
  * Allows for automated testing--to assess deployment targets before continuing

### Blue/Green Deployments

When following the Blue/Green (a.k.a. Red/Black) method, we replicate our "entire" infrastructure for a short time. The replicated infrastructure hosts the new application, while the old infrastructure continues to run until testing is complete and the new stack is adopted. The capabilities to achieve this have been around for a long time, but before the Cloud, it was an incredibly costly deployment method. Now, we can deploy stacks to a whole new environment--allowing for isolated evaluation--and thanks to the Cloud, at minimal costs. Once testing is complete, we switch our application over to the new version and shut down the legacy stack.

![Continuous Delivery Deployment Types: BlueGreen Deployments](https://i0.wp.com/caylent.com/wp-content/uploads/2017/10/BlueGreen-Deployment.png?w=687&ssl=1)

As the image depicts, Blue represents your current environment version, while the new variant you want to deploy is Green. Typically, this happens in the form of a DNS change, though you can deploy Blue/Green by modifying Auto Scaling Groups too.

#### Disadvantages

  * Requires advanced orchestration tooling
  * Some risk as the same database is necessary
  * Incurs some additional cost, though for a short time only
  * Unnatural user traffic will flood your servers--which is not the point for everything to break

#### Advantages

  * Reduced risk profile since infrastructure becomes immutable
  * Offers near zero-downtime
  * The switch is clean and controlled when using a DNS change
  * Process is fully automated and provides a larger validation window
  * It's possible to test the entire environment's health and performance before the switch

### A/B Testing

A/B deployments are virtually identical to Blue/Green, but in this method, we send a small percentage of traffic to our new green environment. This method is capable of switching environments and changing infrastructure, but in a far more precise way than with Blue/Green deployment.

![Continuous Delivery Deployment Types: AB Testing](https://i0.wp.com/caylent.com/wp-content/uploads/2017/10/AB-Testing.png?w=684&ssl=1)

  * In comparison to the aforementioned deployment methods, there are a lot of moving parts
  * Much more complex
  * Requires full automation of everything

#### Advantages

All the benefits of Blue/Green deployments, plus:

  * We can predictably scale capacity and pre-warm production
  * Use to test new features and make gradual assessments on performance, stability, and health
  * We gain customer validation while mitigating blast impact and widespread errors

Selecting your method of deployment comes down to what best suits your business and technical needs. If it makes sense for your application and user base, we highly recommend leveraging A/B testing where possible.

If you're keen to automate this entire process, then we'd like to invite you to check out [Caylent](https://goo.gl/9mi5mD), our SaaS platform that makes it easy to deploy apps, such as WordPress, inside your own cloud. Our DevOps Container Management System automates the entire process covered here and a whole lot more.

Best of all, it is free to begin! Click here to [sign up ](https://goo.gl/R2FFGW)today.

Recently published [Gartner Magic Quadrant Report for Software Test Automation ](https://dzone.com/go?i=265436&u=https%3A%2F%2Fwww.tricentis.com%2Fresource-assets%2Fgartner-magic-quadrant-software-test-automation%2F%3Futm_source%3DDZone_Pre_Roll%26utm_medium%3DText_Ads%26utm_campaign%3DDZoneDevOps%26utm_content%3D2017GartnerMQ)provides an objective benchmark of all test automation solutions based on industry surveys, customer inquiries, product evaluations, and more.

Topics:

continuous delivery ,continuous integration ,docker ,deployment automation ,deployment ,deployment management ,automation ,devops
