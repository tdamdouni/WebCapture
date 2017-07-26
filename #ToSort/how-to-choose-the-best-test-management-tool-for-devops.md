# How to Choose the Best Test Management Tool for DevOps

_Captured: 2017-02-19 at 05:25 from [dzone.com](https://dzone.com/articles/how-to-choose-the-best-test-management-tool-for-de?utm_content=buffer65b8e&utm_medium=social&utm_source=twitter.com&utm_campaign=buffer)_

[Discover how to optimize your DevOps workflows](https://dzone.com/go?i=161129&u=http%3A%2F%2Finfo.saucelabs.com%2Fpaper-the-devops-journey.html%3Futm_campaign%3Ddevopsjourney%2Bwp%26utm_medium%3Dtextlink%26utm_source%3Ddzone-devops%26utm_content%3Darticle) with our cloud-based automated testing infrastructure, brought to you in partnership with [Sauce Labs](https://dzone.com/go?i=161129&u=http%3A%2F%2Finfo.saucelabs.com%2Fpaper-the-devops-journey.html%3Futm_campaign%3Ddevopsjourney%2Bwp%26utm_medium%3Dtextlink%26utm_source%3Ddzone-devops%26utm_content%3Darticle).

Picking the wrong testing tool can be a big waste of time and money. If you choose a test management tool that isn't in tune with where your organization's software developers think their practices are now and where they think they'll be in three to five years, then you're better off sticking to an existing tool or process rather than trying to get your team(s) to switch to the wrong tool.

Most software development shops these days are moving in the direction of DevOps, a set of practices that stresses the importance of collaboration and communication among software developers and other IT professionals. This means that a closer look at tools used at various stages of the DevOps lifecycle should be part of your evaluation process if you want to avoid adding to your company's collection of unused shelfware.

![Image title](https://dzone.com/storage/temp/4094007-devops-diagram-0.png)

> _Figure 1: The merged disciplines of DevOps (source)._

## **The DevOps Toolchain**

Because DevOps is a cultural shift that promotes collaboration between development, QA, and operations (see Figure 1 above), there is no one single product that can be considered the definitive DevOps tool. Often, a collection of tools from a variety of vendors is used in one or more stages of the DevOps toolchain. Almost all DevOps environments use an Agile project management and product development methodology that promotes frequent interaction between an IT department and business users and tries to regularly build and deliver software that meets business users' changing requirements. This means, in effect, building a continuous two-way DevOps software pipeline between you and your customers.

If you are adding [DevOps continuous deployment ](https://devops.com/continuous-delivery-versus-continuous-deploy/)to an existing organization, where you start depends on your current development and testing practices and the bottlenecks in your software delivery process. These bottlenecks can include slow, error-prone manual processes as well as poor-quality, big-bang rollouts that fail in production, leading to unhappy users.

There are several ways to get a handle on the current state of your deployment processes, including using workflow visualization tools like flowcharts and business process maps to break down and understand your CD processes. One of the simplest visual process management tools you can use to help make these kinds of decisions is a Kanban board.

Kanban boards like the one pictured below are typically just sticky notes on a whiteboard that are used to communicate project status, progress, and other issues.

![](https://www.getzephyr.com/sites/default/files/kanban.jpg)

_Figure 2: A Kanban board visually communicates your software delivery process ([source](https://en.wikipedia.org/wiki/Kanban_board#/media/File:Simple-kanban-board-.jpg))._

Many organizations today are also experimenting with Value Stream Maps (VSMs) to better understand the infrastructure changes needed to automate their software delivery process. Borrowed from the Lean manufacturing camp, a VSM is a technique used to analyze value chains, which are the series of events required to bring a product or service to a consumer. Value Chain Mapping is a helpful way to measure your progress in creating a DevOps pipeline, which can be done in two steps:

  1. **The first step measures the efficiency of the different build, deploy, and test stages of the current state of your software delivery.** In doing time measurements (in whatever metric you choose: minutes, hours, or days), you initially try to determine execution time and the wait time in each step. Wait time, in this case, is any non-value added activity such as handoffs, signoffs, manual processes, or delays caused by hardware and software issues.
  2. **The second step measures theefficiency of the different build, deploy and test stages your software delivery target state.** As you remove non-value-adding activity by implementing the core stages of CD (CI, test automation, continuous deployment, etc.), you'll then be able to measure your progress in implementing a DevOps pipeline.

Note: See Mary and Tom Poppendieck's influential book _[Implementing Lean Software Development_](http://www.poppendieck.com/ilsd.htm) for more details on how to apply the concepts of Lean manufacturing and Value Stream Mapping to the software development process.

Whether you use Kanban boards or Value Steam Maps to understand the current state of your deployment processes, the primary goal in implementing a DevOps pipeline is to automate everything, including the following.

## **1\. Build Automation**

Build automation is the first stage in moving toward implementing a culture of DevOps and Continuous Delivery. If your developers are practicing [test-driven development ](http://searchsoftwarequality.techtarget.com/definition/test-driven-development)(TDD), they'll write unit tests for each piece of code they write even before the code itself is written. An important part of the Agile methodology, TDD helps developers think through the desired behavior of each unit of software they're building, including inputs, outputs, and error conditions. New features implemented by developers are then checked into a central code base prior to the software build, which compiles the source code into binary code. With build automation, the software build happens automatically, using tools such as Makefiles or Ant, rather than when a developer manually invokes the complier.

## **2\. Continuous Integration**

In Continuous Integration (CI), developers check code into a shared repository several times a day. Each check-in is then verified by an automated build, allowing teams to detect errors and conflicts as soon as possible. Automation framework and CI tools such as Jenkins and Bamboo are useful in helping build, test and deploy applications automatically when requirements change and thus speeding up the release process.

## **3\. Test Automation**

Another stage in implementing a DevOps deployment pipeline is test automation. Manual testing is a time-consuming and labor-intensive process and, in most cases, also a non-value-adding activity since you're only trying to verify that a piece of software does what it's supposed to do. In addition to doing automated regression testing in a development tool like JIRA, many Agile DevOps teams also practice test-first approaches such as test-driven development (TDD), acceptance test-driven development (ATDD), and [behavior-driven development](https://www.getzephyr.com/resources/whitepapers/how-behavior-driven-development-can-fuel-your-software-testing-program) (BDD).

## **4\. Deployment Automation**

In the last stage of the pipeline, once an application passes all the required tests, it's then released into production. For all intents and purposes, this means releasing every good build to users. The upside of deployment automation is that it allows delivery of new functionality to users within minutes whenever it's needed, as well as instant feedback to the DevOps team that, in turn, allows them to respond rapidly to customer demand. This ties into the concept of using cloud resources and virtual infrastructure to setup and manage your deployment pipeline.

A fully automated deployment pipeline requires the ability to deploy and release any version of a software application to any environment. Doing this effectively requires infrastructure automation where environments (machines, network devices, operating systems, middleware, etc.) can be configured and specified in a fully automatable format. Automating infrastructure this way is called Infrastructure as Code (IaC) and has become increasingly widespread with the adoption of cloud computing and Infrastructure as a Service (IaaS), which relies on virtual machines and other resources that cloud providers like Amazon Web Services and Microsoft Azure supply on-demand from their large pools of equipment installed in data centers.

## **Improving DevOps Feedback Loops**

Selecting the proper tools that support a rapid-paced Agile development lifecycle can be challenging. The key element in DevOps tool selection should be the ability to quickly collaborate across the development, testing, and deployment phases of the DevOps lifecycle. Quick is the operant word here. Quick collaboration requires being able to recognize and improve the feedback loops of all your team(s).

![Image title](https://dzone.com/storage/temp/4094017-feedback-loops.png)

_Figure 3: DevOps is designed to improve feedback frequencies at many different levels ([source](http://en.wikipedia.org/wiki/File:XP-feedback.gif))._

The feedback loop is the time between when a developer writes a line of code and when someone or something executes that code and provides information about how it behaves. If software isn't tested until the very end of the release cycle, as it is in traditional Waterfall development, the primary feedback loop can be measured in months. (See the Release Plan detail in Figure 3 above.)

Luckily, in Agile and/DevOps projects, the software is ready to test almost from the time the first line of code is written. Agile teams typically employ several levels of testing to uncover different types of information.

If your team is practicing Pair Programming, then the observer member of the developer pair should be doing code review, which is intended to improve the overall quality of your software as it's written. Pair Programming is a form of feedback since developers will constantly discuss the best available options with each other. The length of this feedback loop is very short, typically just seconds or minutes. After the code is compiled, automated unit tests check the behavior of individual functions, methods, and code interactions. They're run often and provide feedback in minutes. Similarly, automated integration, system, and acceptance testing check the behavior of the system end-to-end and provide feedback in minutes.

The length of the feedback loop for pair negotiation (also called pair testing) can usually be measured in hours. Issues raised during pair testing can then be discussed at daily standup meetings, which make up their own feedback loop.

[Manual testing](https://www.getzephyr.com/insights/why-manual-testing-still-necessary), particularly manual exploratory tests, take longer to schedule and perform because a human must be available to run them. Also, since exploratory testing is done in a more freestyle fashion than scripted testing, it takes time for the manual tester to design these tests, as well as any follow-up tests needed to confirm the initial test results. The feedback loop for manual acceptance tests can often be measured in days.

Finally, the feedback loops for iteration planning and release planning in a traditional Waterfall application are usually measured in weeks and months.

The shorter you can make any or all of the feedback loops, the more your software delivery process will benefit since these loops enable Agile teams to learn fast and adjust. Similar to the way a software team can increase overall team velocity by normalizing its workload between developers and testers during iteration planning, optimizing each of these individual feedback loops will help a software team deliver higher value with better quality at a much faster pace.

DevOps is all about building, testing, and releasing software faster and more frequently. Unless you're trying to build a DevOps pipeline in a "greenfield" organization without an established coding culture, reducing or amplifying each of the feedback loops above is a good way to minimize the risk and cost of DevOps adoption while building the necessary in-house skills and momentum needed to have widespread successful implementation across your enterprise. For more on this, see [Gene Kim's Three Principles](http://itrevolution.com/the-three-ways-principles-underpinning-devops/) for incremental DevOps adoption.

## **Real-Time Reporting Is Key**

The right test management tool for DevOps is one that enables Agile teams to work collaboratively in the different areas described above -- automated build, automated testing, and automated provisioning of infrastructure for deployment -- in order to speed up the release of high-quality software. Doing that effectively means it should be able to integrate with other project management, issue tracking, and automation tools in your DevOps toolchain. It also should have live reporting features since you need to maintain real-time visibility into the products in your DevOps pipeline. This is important so that information about bugs, inefficiencies, or other issues can be shared and acted on in real-time. If you're a small or medium-sized business (SMB), it also helps to choose a tool that can scale to fit the needs of an enterprise or very large enterprise team. If you get DevOps right, you probably won't be an SMB long.

[Download "The DevOps Journey - From Waterfall to Continuous Delivery"](https://dzone.com/go?i=161130&u=http%3A%2F%2Finfo.saucelabs.com%2Fpaper-the-devops-journey.html%3Futm_campaign%3Ddevopsjourney%2Bwp%26utm_medium%3Dtextlink%26utm_source%3Ddzone-devops%26utm_content%3Darticle) to learn learn about the importance of integrating automated testing into the DevOps workflow, brought to you in partnership with [Sauce Labs](https://dzone.com/go?i=161130&u=http%3A%2F%2Finfo.saucelabs.com%2Fpaper-the-devops-journey.html%3Futm_campaign%3Ddevopsjourney%2Bwp%26utm_medium%3Dtextlink%26utm_source%3Ddzone-devops%26utm_content%3Darticle).

### Like This Article? Read More From DZone
