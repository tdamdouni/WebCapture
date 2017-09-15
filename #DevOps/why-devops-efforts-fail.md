# Why DevOps Efforts Fail

_Captured: 2017-08-24 at 23:19 from [dzone.com](https://dzone.com/articles/why-devops-efforts-fail?edition=319412&utm_source=Daily%20Digest&utm_medium=email&utm_campaign=Daily%20Digest%202017-08-24)_

The Nexus Suite is uniquely architected for a DevOps native world and creates value early in the development pipeline, provides precise contextual controls at every phase, and accelerates DevOps innovation with automation you can trust. [Read how in this ebook](https://dzone.com/go?i=222229&u=https%3A%2F%2Fwww.sonatype.com%2Faccelerate-devops-early-everywhere-at-scale-ebook%3Futm_campaign%3Ddzone%26utm_source%3Dearly%2520everywhere%2520ebook).

The main goal of DevOps is simple: ship software updates frequently, reliably, and with better quality. This goal is somewhat "motherhood and apple pie," and every organization will agree that they want to get there. Many will tell you they've already embarked on the DevOps journey by following some commonly followed frameworks, such as [CALMS](http://whatis.techtarget.com/definition/CALMS).

However, very few will express satisfaction with the results. After speaking to 200+ DevOps professionals at various stages of the adoption lifecycle, we found that organizations generally fall in one of 3 categories:

![Screen Shot 2017-08-06 at 11.01.00 AM.png](http://blog.shippable.com/hs-fs/hubfs/Blog_images/devops-challenges/Screen%20Shot%202017-08-06%20at%2011.01.00%20AM.png?t=1502351241958&width=762&name=Screen%20Shot%202017-08-06%20at%2011.01.00%20AM.png)

We were most interested in groups 2 and 3 since they were actually in the middle of their DevOps journey. When asked to better explain the challenges and roadblocks, here is what we found:

  * 68% said the lack of connectivity between the various DevOps tools in their toolchain was a very frustrating aspect.
  * 52% said a large portion of their testing was still manual, slowing them down.
  * 38% had a mix of legacy and modern applications, i.e. brownfield environments. This created complexity in terms of deployment strategies and endpoints, toolchain, etc.
  * 27% were still struggling with silo'ed teams that could not collaborate as expected.
  * 23% had limited access to self-service infrastructure.
  * Other notable pain points included finding the right DevOps skillset, difficulty managing the complexity of multiple services and environments, lack of urgency/budget, and limited support from executive leadership.

Let us look at each of these challenges in greater detail.

## #1: Lack of Connectivity in the DevOps Toolchain

There are many DevOps tools available that help automate different tasks like CI, infrastructure provisioning, testing, deployments, config management, release management, etc. While these have helped tremendously as organizations start adopting DevOps processes, they often do not work well together.

![devops-islands-of-automation.png](http://blog.shippable.com/hs-fs/hubfs/Blog_images/devops-challenges/devops-islands-of-automation.png?t=1502351241958&width=914&name=devops-islands-of-automation.png)

As a classic example, we spoke to a Principal DevOps engineer whose team uses [Capistrano](http://capistranorb.com/) for deployments. When asked how he found out about a new application version or configuration change, he said the Test and Ops teams opened JIRA tickets and included the information required to run Capistrano. He then manually updated his scripts before running them. This process took several hours and needed to be carefully managed since the required config was manually transferred twice, once when entered into JIRA and second, when copied it to Capistrano.

This is one simple example, but this problem exists across the entire toolchain. Propagating state and other information required to execute dependent tasks across tools is handled very poorly today.

Smaller organizations get around this problem by writing custom scripts that glue their toolchain together. This works fine for a couple of applications, but quickly escalates to spaghetti hell since these scripts aren't written in a standard fashion. They are difficult to maintain and often contain tokens, keys and other sensitive information. Worse of all, these scripts are highly custom for each application and cannot be reused to easily scale automation workflows.

For most serious organizations, it is an expensive and complex effort to build this homegrown "DevOps glue" and unless they have the discipline and resources of the Facebooks and Amazons of the world, it ultimately becomes a roadblock for DevOps progress.

Continuous Delivery is impossible to achieve when the tools in your DevOps toolchain don't collaborate and you manage dependencies manually or through custom scripts.

## Challenge #2: Lack of Test Automation

Despite all the focus on [TDD](https://en.wikipedia.org/wiki/Test-driven_development), most organizations still struggle with automating their tests. If the testing is manual, it is almost impossible to execute the entire test suite for every commit, becoming a barrier for Continuous Delivery. Teams try to optimize this by running a core set of tests for every commit and running the complete test suite only periodicially. This means that most bugs are found later in your software delivery workflow and are much more expensive to find and fix.

![bug-fix-efficiency.png](http://blog.shippable.com/hs-fs/hubfs/Blog_images/devops-challenges/bug-fix-efficiency.png?t=1502351241958&width=1008&name=bug-fix-efficiency.png)

Test automation is an important part of the DevOps adoption process and hence needs to be a top priority.

## Challenge #3: Brownfield Environments

Typical IT portfolios are heterogeneous in nature, spanning multiple decades of technology, cloud platform vendors, private and public clouds in labs and data centers, all at the same time. It is very challenging to create a workflow that spans across these aspects since most tools work with specific architectures and technologies. This leads to toolchain sprawl as each team uses the toolchain best serving their needs.

The rise of Docker has also encouraged many organizations to develop microservices-based applications. This increases the complexity for DevOps automation since an application now needs 100s of deployment pipelines for heterogeneous microservices. Microservices also lead to dynamic application lifecycles where each microservice is deployed and scaled independently, so the scheduling and coordination required across teams goes up exponentially.

## Challenge #4: Cultural Problems

Applications evolve across functionals silos. Developers craft software, which is stabilized by QA, and then deployed and operated by IT Operations. Even though all these teams are expected to work together and collaborate, they often have conflicting interests.

Developers are driven to move as fast as they can and build new stuff. QA and Release management teams are driven to be as thorough as possible, making sure no software errors can escape past their watchful eyes. Both teams are often gated by SecOps and Infrastructure Ops, who are incentivized to ensure Production doesn't break. Governance and compliance also play a role in slowing things down. Cost centers are under pressure to do more with less which leads to a culture that opposes change, since change introduces risk and destabilizes things, which means more money and resources are required to manage the impact.

This breakdown across functional silos leads to collaboration and coordination issues, slowing down the flow of application changes.

Some organizations try to address this by making developers build, test and operate software. Though this might work in theory, developers are bogged down by production issues, and a majority of time is spent on operating what they built last month as opposed to innovating on new things. Most organizations try to get all teams involved across all phases of the SDLC, but this approach still relies on manual collaboration.

Automation is the best way to broker peace and help Dev and Ops collaborate. But as we see in other challenges, ad-hoc automation itself can slow you down and introduce risk and errors.

## Challenge #5: Limited Access to Self-Service Infrastructure and Environments

Virtual machines and cloud computing have transformed the process of obtaining the right infrastructure on-demand. What previously took months can now be achieved in a few minutes. IaaS providers like AWS have hundreds of machines with flexible configurations and many options for pre-installed OS and other tools. Tools like Ansible, Chef, Puppet help represent infrastructure-as-code, which further speeds up provisioning and re-provisioning of machines.

However, obtaining infrastructure is still a problem in many organizations, especially those running their own data centers or those that haven't embraced the Cloud yet.

## We Need More From DevOps

A popular DevOps framework describes a CALMS approach, consisting of **C**ulture, **A**utomation, **L**ean, **M**easurement, and **S**haring. The DevOps movement started as a cultural movement, and even today, most implementations focus heavily on culture.

While culture is an important part of any DevOps story, changing organizational culture is the hardest thing of all. Culture forms over a period of time due to ground realities. Ops teams don't hate change because they are irrational or want to be blockers. Over the years, they've taken the heat every time an over-enthusiastic Dev team tried to fast track changes to production without following every step along the way. Seating them with Devs might help make the work environment a little friendlier but it doesn't address the root cause, no matter how many beers they have together.

![Screen Shot 2017-08-06 at 2.57.43 PM.png](http://blog.shippable.com/hs-fs/hubfs/Blog_images/devops-challenges/Screen%20Shot%202017-08-06%20at%202.57.43%20PM.png?t=1502351241958&width=985&name=Screen%20Shot%202017-08-06%20at%202.57.43%20PM.png)

In my next blog in this series, I will explore an automation focused approach to DevOps, and see how automation can actually help drive other aspects like Culture, Lean, Measurement, and Sharing.

The DevOps Zone is brought to you in partnership with Sonatype Nexus. See how the Nexus platform infuses precise open source component intelligence into the DevOps pipeline early, everywhere, and at scale. [Read how in this ebook](https://dzone.com/go?i=222230&u=https%3A%2F%2Fwww.sonatype.com%2Faccelerate-devops-early-everywhere-at-scale-ebook%3Futm_campaign%3Ddzone%26utm_source%3Dearly%2520everywhere%2520ebook).
