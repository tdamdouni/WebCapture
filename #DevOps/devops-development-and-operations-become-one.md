# DevOps: Development and Operations Become One

_Captured: 2018-08-29 at 06:56 from [dzone.com](https://dzone.com/articles/devops-development-and-operations-become-one)_

Easily enforce open source policies in real time and reduce MTTRs from six weeks to six seconds with the Sonatype Nexus Platform. See for yourself - [Free Vulnerability Scanner.](https://dzone.com/go?i=290455&u=https%3A%2F%2Fwww.sonatype.com%2Fsoftware-bill-of-materials%3Futm_campaign%3Ddzone%252520-%252520AHC%26utm_source%3DDZone%252520-%252520AHC%2525202018%26utm_medium%3DDZone%252520-%252520AHC%2525202018)

If you are a consumer of modern software, including Apps on your smartphone, you are a beneficiary of what is known in the software industry as DevOps. Bridgera's own VP of Enterprise IoT Solutions, Joydeep Misra, provide and explanation of what DevOps means and how it is an enabling process for modern Software-as-a-Service and Agile development methodology.

## **DevOps as a Concept**

Prior to Software being available as a service, the software provider maintained a Development team with a quality assurance function. They were responsible for developing software and "shipping" it to the consumer. Operations, including infrastructure setup and maintenance (servers, datacenter etc), software installation, and upgrades, was the responsibility of the consumer, or the consumer's IT.

With the advent of software as a service (SaaS), the software provider now assumes responsibility for operations, in addition to development and QA. This shift of responsibility from consumer to provider has been eye opening to the software industry. In the past, a software company could blame issues on the incompetence of their customer's IT, now since there in no more shifting of blame, new operational processes have evolved, one of these being DevOps, which is a unification of software development (including QA) and software operations allowing the developers and the operations teams to be more efficient through collaboration and adoption of a few established processes.

While the early pioneers of DevOps processes where progressive SaaS companies, we now see these techniques performed by service providers as well as IT organizations who may have an end-to-end responsibility for a software product.

## **How Is DevOps Related to Agile?**

The traditional "Waterfall" software development model is slow and does not require a lot of interaction or collaboration among the teams. Requirements are passed onto developers, developers write code and pass to the testing team, testing approves the code and passes to the operations to deployment.

The Agile software development process makes the journey from conception to production much faster by implementing quick review cycles from the very beginning. Almost every framework of Agile (Scrum, Kanban, Lean, Extreme Programming) uses an iterative approach to build a software product in small steps. A usable product is expected at the end of every iteration for review and feedback. This requires very frequent releases of a software product. Every software release cycle requires 1) integration of new code to the existing codebase, 2) a compile+build process, 3) deployment of the newly built software with all the dependencies, and 4) unit integration and regression testing to ensure quality.

![](https://bridgera.com/wp-content/uploads/2018/07/Task.png)

Small iterations and quick review cycles demand a lot of collaboration among the software team members. The DevOps process streamlines the development, QA, and deployment activities and becomes efficient through automation tools and processes.

### **What Tools Are Used in DevOps?**

DevOps has a place in almost every aspect of software development. Due to the high adoption of Agile software development, DevOps processes have become very popular.

Given Agile's inherent quick turnaround nature, Continuous Integration, Continuous Build, and Continuous Deployment processes were introduced to help quickly release software products with better quality and more predictable results. There are a variety of DevOps tools in existence to support and automate different development and operation tasks.

  * **Source Code Repository** \- Developers keep their source code in source code repositories. It allows version control of the source code files and allows the developers to compare and merge code from different developers. Source code repositories play an important role in facilitating continuous integration by allowing the developers to check in the code more frequently, making sure the incremental changes do not break the existing codebase. There are many source code repositories to choose from, including Git, Bitbucket, Mercurial, and TFS.

  * **Build Server** \- Build servers get the code from a source code repository and build the executables for deployment. Build servers facilitate Continuous Build process by automatically downloading the code from source code repository and building the product using the pre-configured dependencies. The most popular build servers out there are Jenkins, Bamboo, and CruiseControl.

  * **Automated Testing** \- It is important to test the software product after the build process to make sure there are no obvious errors before releasing the code to the users. Automated regression testing helps in ensuring the quality of a software product. Test script execution plays an important role in the DevOps pipeline and can be invoked from the build server after a successful software build. Popular test automation tools are - Selenium, TestingWhiz, SahiPro, TestComplete, and IBM Rational Functional Tester.

  * **Configuration Management** \- Configuration management is important to ensure the software product will run in all the environments. Tools like Puppet, Chef, Ansible, and Salt Stack helps in managing the configurations. Solutions like Docker "containerize" code along with the configurations, helping to move code easily from one server to another.

## **What Projects Are Best Suited for DevOps?**

Almost all software projects can benefit from DevOps. As discussed above, DevOps is best suited for Agile projects where the software team is under pressure to release new builds every 2 to 3 weeks or sooner. Large software teams have their own challenges. Working with remote teams make collaboration even more difficult. DevOps processes help these large remote teams overcome software delivery difficulties and ensure quality. DevOps is definitely required to streamline the software delivery process when there are different teams responsible to take care of different tasks (Development, QA Testing, IT Operations) and where there is a lot of collaboration needed to ensure error-free delivery.

## **Are Any Projects Poorly Suited for DevOps?**

DevOps can be an overkill for very small projects, particularly proof-of-concept type work. Most of the time these projects do not need strong processes to ensure quality. Many times only one person or a few people take care of everything in these projects. They may get the things done quicker by themselves without going through the process of establishing a DevOps pipeline for their project.

## **How does Bridgera Use DevOps?**

At Bridgera, we develop software solutions for Internet of Things use cases. IoT solutions are complex because the stack involves a lot of different skills like database development and management, back-end programming for IoT platforms, web application, and mobile application development. We use an in-house development, QA, and operations team to take care of every aspect of an end-to-end IoT software solution. We apply Agile project management methodologies, collaborate with our customers and allow them to provide important feedback continuously via frequent review cycles (sprint planning/ review meetings).

We use virtual cloud infrastructure to host our software solutions and use DevOps to streamline the development, QA, and release processes.

Our team works on multiple customer projects at the same time. Without a good Source Code management and integration process, it would be nearly impossible to deliver bug-free code. We use Git and Bitbucket as Source Code Repository. We involve the QA team from the beginning to write unit and integration test cases and use Selenium to write automated Regression test cases. We use Jenkins as our build server use build tools like Maven or MSBuild to automate the build process. After a successful build, we use automated regression tests to ensure quality and then deploy the product to the target environment.

DevOps is a crucial aspect of modern software development strategies. It will become even more prevalent as more teams adopt Agile as their go-to software development methodology. It may not be suitable for everything you do, but educating yourself on the concept of DevOps will make it much easier to succeed in the world of software development.

Automate open source governance at scale across the entire software supply chain with the Nexus Platform. [Learn more.](https://dzone.com/go?i=290456&u=https%3A%2F%2Fwww.sonatype.com%2Fwp-enforce-open-source-policies-with-confidence)
