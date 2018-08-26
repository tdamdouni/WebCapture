# The Ultimate Guide to Cloud-Native Jargon

_Captured: 2018-08-07 at 19:13 from [dzone.com](https://dzone.com/articles/the-ultimate-guide-to-cloud-native-jargon?edition=385338&utm_source=Zone%20Newsletter&utm_medium=email&utm_campaign=cloud%202018-08-07)_

Insight into the right steps to take for migrating workloads to public cloud and successfully reducing cost as a result. [Read the Guide](https://dzone.com/go?i=302423&u=https%3A%2F%2Fwww.bmc.com%2Fforms%2Ffive-steps-cloud-cost-optimization-forbes-ebook.html%3FproductInterest%3Dtruesight%252520cloud%252520cost%252520control).

The definition of what makes something a cloud-native application can be a little (pardon the pun) cloudy. This lack of clarity is curious given that [by 2020, it is predicted that the "Cloud Shift" will affect more than $1 trillion in IT spending](https://www.gartner.com/newsroom/id/3384720), making cloud computing the next major technological disruptor.

With this much money at stake, one would hope that everyone involved in the cloud ecosystem could speak the same language and come to a consensus on the correct usages. But, as with any evolving concept, there are overlapping terms and ideologies, creating a whole lot of jargon!

We have tried to address not only how we define the various elements of cloud-native here at MojoTech but have lumped the jargon into categories to help give more context for how all the elements work together.

## The Four Stages of Cloud Maturity

### **On-Premise**

Software that is installed and runs somewhere in your organization's building, rather than at remote data center or in the cloud.

### **Cloud-Enabled**

The first step toward cloud maturity. Cloud-enabled applications have been moved to the cloud, but are still developed for deployment in a traditional data center. See "Lift and Shift" below.

While one benefit of cloud-enabled applications is short-term cost reduction (affectionately called "your mess for less,"), the benefits you can reap in the long-term by taking full advantage of building cloud-native applications outweigh simply re-hosting and calling it a day.

### **Cloud-Optimized**

Cloud-Optimized Applications take Cloud Applications one step further, optimizing them for access to more cloud features without having to be re-developed as cloud-native applications. Some of these features might include the use of third-party APIs for services like email, file storage, SMS, analytics, performance metrics, logging, search, and even data-stores.

A hybrid between applications that were moved to the cloud and applications that were built for the cloud, some of the benefits include the ability for a continuous delivery of code (i.e., faster time to production,) and the ability to scale both vertically and horizontally.

### **Cloud-Native**

The Holy Grail. Cloud-Native Applications are the end goal for modern software development.

These applications are built from the ground up to incorporate best practices for efficiency, delivery, and availability. Utilizing features of the cloud allow these applications to operate consistently across devices, platforms, and providers.

## Some Cloud Crowd Favorites

### **12-Factor Apps**

The concept of the 12-factor app is not new. The term is essentially a fancy way of branding a methodology MojoTech, as well as any good developer, has been following for years to build modern web-based applications.

There are 12 fundamentals which you can [read in-depth](https://12factor.net/) if you're interested in the nitty-gritty details.

### **Lift and Shift**

"Lift and Shift" is a cloud migration strategy whereby an organization essentially lifts up their existing architecture and re-hosts it in a cloud environment, without optimizing the application for a cloud environment features. This is the opposite of re-architecting an application to live natively in the cloud.

If a choice between "Lift and Shift" and doing nothing, we advocate for making the shift promptly. But it's often better to skip this step and determine how your organization can allocate the resources and invest in a long-term cloud migration strategy instead.

### **Replatforming**

A step further than "Lift and Shift" whereby an organization makes a few adjustments to take advantage of cloud-native features but avoids a complete architecture overhaul. This might be appropriate when you only want to make incremental changes including automating deploy processes, offloading functionality to third-party APIs, or moving environmental dependencies from code to environment variables.

Replatforming is probably the best approach whenever you have an existing production app already in the cloud.

### **DevOps**

For this posts purposes, Development Operations refers to the activity, not the role.

DevOps are at the core of the rise of cloud computing. As you build cloud-native software, you end up with lots of smaller apps that talk to each other, which means you need software to manage all of the little bits. You get many benefits from building microservices, but they come at the cost of infrastructure complexity. DevOps manages that complexity.

Without DevOps, you may end up with an application that has all the correct business features, but which you can't deploy and maintain reliably.

### **Digital Transformation**

This is a hot term that the enterprise industry, in particular, just can't seem to get away from. Large, slow-moving organizations with legacy infrastructure and architecture are finding themselves at odds with modern software development practices. And it's hurting business.

The "transformation" often needs to start at an organizational level, not a technological one. Siloed departments, employees with highly specialized, yet outdated skill sets, and a management team that hasn't the first idea how to turn things around (or aren't given the support to do so) are more damaging to an organization's future than whether they are using the Waterfall Methodology.

When it comes to "Digital Transformation" there is a lot to unpack. But if you want to think about it as it relates to software development and design, start by reading [Why Products Built By Large Teams Fail So Often](https://www.mojotech.com/blog/why-products-built-by-large-teams-fail-so-often/).

## Cloud Deployment Methods

### **Containerization**

Just as virtual machines allow multiple operating systems to live on one machine, containers allow multiple apps to live on one virtual machine.

With containerization, applications are bundled with dependencies like libraries, configuration files, and binaries to expedite the process of deploying new applications and deploying updates to existing ones.

### **Microservices**

Microservices in Cloud-Native Applications are services separated out to address a specific task. Since these services are loosely coupled with the underlying application, they can be updated or repaired without impacting other services. Each microservice has an API, an interface with the rest of the software system, which needs to be designed, implemented, and maintained.

### **Orchestration**

Orchestration was introduced to the software development process to streamline the process of manually provisioning and configuring applications.

With DevOps time constrained by setting up new web servers, databases, and load balancers, orchestration creates efficiency by automating DevOps processes.

### **Continuous Integration**

The merging all of your code, back to the main branch, continually. Changes are then validated through automated testing to avoid integration issues that cause teams to have to untangle weeks upon weeks of work.

### **Continuous Delivery**

Applications can easily be replicated to create a more efficient deployment workflow. While code can be updated through a code repository, the environment and configuration can just as easily be re-created by just cloning existing applications, and publishing them as needed.

From here, developers can use their individual workstations to write code, push to staging/development servers, and then ultimately have the code from development pushed to production.

### **Continuous Deployment**

When the automated tests pass, that code is shipped out to real users, using orchestration tools. This accelerates the feedback loop with customers which is vital for exceptional product development. By getting rid of the "Release Day" mode of working, developers can see their work go live in minutes and focus on what matters most to users and product owners.

## Cloud Computing Service Models

### **IaaS**

A distant cousin of SaaS, Infrastructure-as-a-Service is a model of cloud computing in which the vendor hosts or "rents out" virtualized computing resources, as well as network and storage resources, and provides them to a customer. Over time, this greatly reduces a business's capital expenditures (buying and maintaining physical hardware). The consumption-based billing model becomes an operational expenditure instead.

_Example: Amazon Web Services, Digital Ocean, Rackspace, Microsoft Azure_

### **PaaS**

Platform-as-a-Service is a model of cloud computing in which a vendor provides the hardware and software tools necessary to create, deploy and manage applications at scale, as a service. Developers write the application code and it's the platform's responsibility to manage the infrastructure components necessary to run the application. Benefits include reduced development cycles and some limitations can include limited language runtimes, libraries, and features.

_Examples: Pivotal Cloud Foundry, Heroku, EngineYard_

### **SaaS**

Software-as-a-Service is the most widely used model of cloud computing. A third-party provider hosts, manages, and stores an application, making it available to paying customers, typically via a subscription basis.

_Examples: Gmail, Spotify, Salesforce, Skype, GoToMeeting_

Confused about which infrastructure components you need to manage and when? Here's a helpful diagram:

![Cloud Infrastructure Management](https://www.mojotech.com/blog/images/uploads/cloud-infrastructure-management.png)

## Cloud Computing Benefits

### **Fault-Tolerance**

Cloud-Native Applications reduce the risk for single points of failure. Unexplained performance issue? Applications can automatically relocate to different compute and memory resources.

Worried about disk failure? Cloud providers can hot swap out startup disks in the event of a failure. All of these safety features increase business continuity while decreasing the need for IT staff to intervene.

### **Scalability**

Scalability is the ability of a process, system, or framework to handle a growing workload. In other words, a scalable system is adaptable to increasing demands. The ability to scale on demand is one of the biggest advantages of cloud computing.

### **Elasticity**

The ability of a system to adapt workload changes to match demand. This is a key cost-savings feature as it prevents over or under-provisioning. Under-provision and you might compromise your users' experience, and even lose them, by serving up a slow website. Over-provision and you'll make your service provider very happy by paying them for more resources than you're actually using.

[TrueSight Cloud Cost Control ](https://dzone.com/go?i=302424&u=http%3A%2F%2Fwww.bmc.com%2Fit-solutions%2Ftruesight.html)provides visibility and control over multi-cloud costs including AWS, Azure, Google Cloud, and others.
