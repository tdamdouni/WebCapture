# Serverless Computing vs. Containers

_Captured: 2018-09-05 at 07:33 from [dzone.com](https://dzone.com/articles/serverless-computing-vs-containers?edition=393191&utm_source=Daily%20Digest&utm_medium=email&utm_campaign=Daily%20Digest%202018-09-04)_

Insight into the right steps to take for migrating workloads to public cloud and successfully reducing cost as a result. [Read the Guide](https://dzone.com/go?i=302423&u=https%3A%2F%2Fwww.bmc.com%2Fforms%2Ffive-steps-cloud-cost-optimization-forbes-ebook.html%3FproductInterest%3Dtruesight%252520cloud%252520cost%252520control).

Serverless computing has seen a significant adoption over the last couple of years, with all the major public cloud providers enabling serverless architectures. AWS Lambda, Azure Functions, and Google Cloud Functions provide an abstraction layer to deploy small pieces of code instead of monolithic applications and further simplifies public cloud consumption. But, serverless architecture is not suitable for all the applications and has its own issues that need to be considered.

Virtual machines (VMs), containers, and serverless are all different mechanisms of resource virtualization and have evolved to simplify and manage resources. Moving from one mechanism to another generally involves a significant workflow transformation and care needs to be taken before selecting the right computing model.

Traditionally, VMs have been the _de facto_ standard for infrastructure virtualization. Hypervisors are used to virtualize the hardware resources and the operating system is unaware of underlying resource management. For a given hypervisor, each VM has its own operating system and hypervisor virtualizes hardware such that each VM believes it has a dedicated set of resources.

With the booming popularity of containers came a new way of resource utilization by virtualizing the operating system itself instead of the physical hardware. VMs consist of the entire operating system along with the application-specific libraries, but containers comprise only the libraries needed to run the applications with a single operating system being shared by all the containers.

Enter serverless computing. Serverless computing is another abstraction on top of the operating system which provides a mechanism to run the application in a lot of smaller pieces. It provides functions or modules to execute application tasks that can be executed on-demand without worrying about underlying operating system and hardware infrastructure. These tasks are generally short-lived and run periodically as per the application requirements. Similar to the way cloud computing need physical hardware, serverless computing need servers as well for any application execution.

Benefits seem boundless; adopting serverless lowers costs, speeds time to deployment, increases scalability and decreases management time for overworked IT teams. Serverless is also great for supporting various microservices and popular with developers for DevOps.

A [study conducted last year by New Relic](https://newrelic.com/serverless-dynamic-cloud-survey?content=eBook) revealed 70 percent of enterprises have migrated a significant number of workloads to the public cloud. From this group 39 percent were using serverless, 40 percent used containers and 34 percent used some sort of container orchestration. This points to how the adoption of serverless technologies now matches that of containers, but what is not yet quite clear is the extent of use in production applications.

Another study from [Cloudability](http://get.cloudability.com/ebook-state-of-cloud-2018.html) shows adoption of containers and serverless computing services is growing in the triple digits quarter to quarter, based on data in late 2017. Specifically, for Amazon Web Services users, container adoption grew 246 percent during the fourth quarter of 2017, and 206 percent the quarter before that, with most customers leaning toward Kubernetes as a popular service. That study also showed huge growth in adoption of serverless computing among cloud users, growing by 667 percent among the sites tracked. Serverless continues to be attractive to organizations since it doesn't require management of the infrastructure as companies continue to build cloud-native architectures.

Let's consider two different use cases to figure out the pros and cons of serverless and container-based architectures.

## **Restaurant Review and Reservation Application**

Our application design will consist of two databases that store information related to restaurant reviews and reservation transactions, respectively. Our application browser should be able to perform restaurant searches based on certain keywords, submit restaurant reviews and reserve a table. Serverless architecture for such an application can be designed as shown below:

![](https://i0.wp.com/containerjournal.com/wp-content/uploads/2018/08/containersserverlesspic1.png?resize=800%2C302&ssl=1)

Database as a service (DBaaS) is utilized for restaurant details and reservations using DynamoDB and RDS. AWS Lambda provides FaaS (functions as a service) for executing these tasks:

  * Restaurant search
  * Restaurant review
  * Restaurant reservations

Amazon API gateway is being used as the HTTP server, redirecting requests to above Lambda functions. These functions are ephemeral tasks that can be invoked on-demand and terminated after execution. Serverless architecture for this application removes the need for physical servers, sysadmins and over-provisioning of resources for handling the peak user traffic scenario.

Container-based architecture can also be used for this implementation, but it will involve an overhead of another container orchestration layer along with an interface that can handle restaurant tasks and replaces the API gateway. Serverless architecture for this use case allows businesses to introduce new features by simply adding new Lambda functions and scale application traffic on-demand.

## **Continuous Integration and Continuous Deployment (CI/CD) Pipeline **

The CI/CD pipeline is a key component of delivering modern software frequently in small increments. As part of the CI/CD pipeline, software needs to be rebuilt whenever any code change is made, execute regression and function tests and redeploy software if needed. This seems like a perfect fit for serverless architecture, which can be developed as shown below.

![](https://i1.wp.com/containerjournal.com/wp-content/uploads/2018/08/containersserverlesspic2.png?resize=800%2C575&ssl=1)

If the build task starts taking a large amount of time or testing involves long-running operations, serverless architecture might not work. All the public FaaS providers such as AWS, Azure and Google Cloud have a maximum duration of time (between 300 and 540 seconds) that is allowed to run any given task. For such unpredictable long-running tasks, it is beneficial to run using a container-based architecture that can shut down tasks after execution at any given point of time. Container-based architecture for the CI/CD pipeline can be built as shown below:

![](https://i1.wp.com/containerjournal.com/wp-content/uploads/2018/08/containersserverlesspic3.png?resize=800%2C504&ssl=1)

It involves deploying container orchestrator such as Kubernetes that can efficiently run containers in a distributed environment. The infrastructure orchestration tool Chef is used to coordinate with Kubernetes and schedule containers when needed. Users still have the option of eliminating server management by running containers in the cloud.

## **Finding the Balance in the Enterprise **

Comparing containers vs serverless computing is like comparing running an application on-premises in the local data center or running it in the cloud. At the end of the day, someone must manage the infrastructure and pay for it. Containers are best suited to build a serverless computing framework and relieve the end user of infrastructure management-but comes at a cost.

Users need to find a balance between the cost and complexity such that serverless computing can justify the extra cost of offloading infrastructure management. Serverless computing and FPaaS (function platform as a service) are best suited for running applications in the public cloud and containers are useful in transforming on-premises hardware resources into a private cloud.

The studies don't lie-both containers and serverless computing are booming, and here to stay. Which one will win in the end?

[TrueSight Cloud Cost Control ](https://dzone.com/go?i=302424&u=http%3A%2F%2Fwww.bmc.com%2Fit-solutions%2Ftruesight.html)provides visibility and control over multi-cloud costs including AWS, Azure, Google Cloud, and others.

Topics:

containers ,containers and containerization ,serverless ,virtual machine ,docker containers ,aws ,azure ,gcp ,cloud
