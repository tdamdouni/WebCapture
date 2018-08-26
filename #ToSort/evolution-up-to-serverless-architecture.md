# Evolution up to Serverless Architecture

_Captured: 2018-03-06 at 18:25 from [dzone.com](https://dzone.com/articles/evolution-up-to-serverless-architecture-1?edition=366208&utm_source=Zone%20Newsletter&utm_medium=email&utm_campaign=cloud%202018-03-06)_

###  Take a brief history lesson on the evolution of serverless, then see if the advantages outweigh the disadvantages enough for your next project. 

Get the Metrics Collection and Monitoring Essentials [tutorial collection](https://dzone.com/go?i=274448&u=https%3A%2F%2Fwww.digitalocean.com%2Fcommunity%2Ftutorial_series%2Fmetrics-collection-and-monitoring-essentials%3Futm_medium%3Dbumper%26utm_source%3Ddzone%26utm_campaign%3Dbrand%2Bsimplicity%2Bat%2Bscale%26utm_content%3Ddistributed%2Bmicroservices%2Bdeployments). A 4-part tutorial series from [DigitalOcean](https://dzone.com/go?i=274448&u=https%3A%2F%2Fwww.digitalocean.com%2F%3Futm_medium%3Dbumper%26utm_source%3Ddzone%26utm_campaign%3Dbrand%2Bsimplicity%2Bat%2Bscale%26utm_content%3Dmetrics%2Bcollection%2Bmonitoring).

This post will cover the software architecture evolution up to the new concept called "Serverless" and the basics of the pattern. When we look at the term serverless, it sounds like it is achieving functionality of a server without a server. Yes, it means that _you_ do not have a server, but in reality, someone does. Severless techniques are available with the big players already. For example, Amazon AWS Lambda, Google Cloud Functions, and Windows Azure Functions can be identified as main competitors at the moment.

### **Evolution**

  * **On premise monoliths > Service Oriented Architecture > Cloud > Microservices Architecture > Serverless Architecture**
  * **Physical server > Virtual machines > Containers**

Serverless can be identified as a result of marriage of Cloud and Microservices Architecture (MSA). Let's see how we got there.

Enterprise software architecture traveled through quite a few steps in the past. Software used to be a huge monolith that developed and added the functionality continuously to one. Most of the time these software were installed in physical and resource-heavy, mainframe type servers. Then it started to evolve through different phases of architecture as people started to invent new patterns to achieve more flexibility, agility, and productivity, and Service Oriented Architecture (SOA) was born as a result.

SOA was boosted through cloud techniques. REST introduced a simple way to achieve SOA with far less complex specification than SOAP and provided freedom of using different message types like JSON. This elevated the embracing of SOA in the industry. Adoption of virtual machines was also helping the SOA as it catered dynamic requirements suited for that architecture.

MSA proceeded and many believed it is SOA done right. Serverless is breaking the services finer and it is a great way to do things flexibly and cleanly. But why did industry wait this long to adopt such paradigms? Before the huge popularity of MSA, which should be mainly attributed to the rise of technologies such as containers, running a server was not an low overhead task. Therefore, it didn't allow the systems to create and delete of servers faster and dynamically. VM technologies were not up to the mark for such advance requirements. The container adoption led to such a valuable string of architecture patterns we see today.

### **Advantages**

This section will discuss the advantages of serverless architecture compared to the earlier pieces of the architectural chain. Some of the following advantages will overlap with the MSA advantages as they are close relatives.

  * **Choice of technology** -- You can pick and choose different languages for different functions as it suites.
  * **Choice of architecture** -- You might have decided to use serverless, but it doesn't have to be serverless only. You may decide to implement a set of services as serverless, another set in on premise microservices, or using your legacy system.
  * **Faster turnaround and best for marketing** -- Think about changing an existing service to add functionality and adding the function by creating a completely new service, independently. The later will save you lots of time. It avoids worrying about the whole service, and lets you get the function ready faster. You can market your new feature within days, if not in hours.
  * **Never pay for idle** -- You will not need to pay anything if there were no traffic. No cold servers will be maintained. Servers can be spawned milliseconds when the traffic starts.
  * **Faster and law-cost scaling** -- Simple/small functions and MSA-like architecture helps scale the services horizontally, quickly. Low boot time helps make capacity available within milliseconds and improve your availability numbers of the platform. You can handle steep spikes smoothly without worrying about availability.
  * **Simplified team responsibilities** -- Different teams working on different parts of a complex application will bring in complicated and time consuming discussions and interactions. With the clear borders in defined APIs, teams will breathe a little easier on those occasions.
  * **Offloading infrastructure worry** -- Before serverless, engineers overlook all the aspects of running the service online. This means that they have to optimize the node resources according to the capacity planning, setup analytics, handle scaling and many more. Serverless providers usually accommodate all in one bundles including all spare parts of the ecosystem.
  * **Saving the world** -- As you strive to keep your platform available with most 9s possible, you may have to run servers every region in the world and keep a resource margin to cover sudden traffic spikes. In the process, the world has to pay the price with the energy waste and resource allocation which may be idle at times. Serverless utilizes the resources best and saves energy without wasting for idled servers.

### **Disadvantages**

We can see a lot of advantages over disadvantages in this architecture. However, we can identify several drawbacks when it is compared to it's architectural ancestors.

  * **Less control** -- As the services are managed in a cloud belongs to a 3rd party cloud provider, we might have to depend on them. Moving to a new platform would be costly and you might have to stick to the vendor despite of the higher price or API changes. One could use workarounds such as getting your code in a container and apply AWS Lambda.
  * **Architectural complexities** -- People might mix and match architectures, but they will get their share of complexity in that package. It will not be a smooth ride handling different architectures and different parties involved.
  * **Not for long-running applications** -- As these functions are configured as short lived and dynamic functions, it might not suit your application if long running operation is required.
  * **Privacy and multi-tenancy** -- Mostly these functions may run in a same application server for several different customers. There could be attackers exploiting any security holes in the system.

### **Types of Use Cases**

Pretty much any functionality that you want to get quickly up and running can be identified as a serverless use cases. It it impossible to name all the cases this will be useful. Some characteristics of use cases can be:

  * New architecture opportunities -- You may want to break your single app to a lot of functions or you may have a bunch of utility, stateless functions which are not related to each other. Serverless can be your answer.
  * **Adding secure functions to insecure components** -- If there is a function you want to run securely, which cannot be done in your client app, you can simply create a Serverless app and use it with security enabled API.
  * **New ad-hoc functions to current architecure** -- Say you already have your architecture implemented and running using SOA or MSA architectures, and you want to introduce a small, yet completely new function. You can do a serverless function quickly and deploy.

Getting Started with Kubernetes: [A Webinar Series](https://dzone.com/go?i=280427&u=https%3A%2F%2Fwww.digitalocean.com%2Fcommunity%2Ftutorials%2Fwebinar-series-getting-started-with-kubernetes%3Futm_medium%3Ddisplay%26utm_source%3Ddzone%26utm_campaign%3Dbrand%2Bsimplicity%2Bat%2Bscale%26utm_content%3Dbumper_webinar%2Bkubernetes%2Bdzonecloud) brought to you by DigitalOcean

Topics:

serverless architecture ,evolution ,advantages and disadvantages of serverless ,cloud ,msa ,soa ,microservices
