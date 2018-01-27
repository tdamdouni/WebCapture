# API Management Design Patterns for Digital Transformation

_Captured: 2018-01-26 at 18:18 from [dzone.com](https://dzone.com/articles/api-management-design-patterns-for-digital-transfo-1?utm_source=Top%205&utm_medium=email&utm_campaign=Top%205%202018-01-263)_

Digital Transformation (DT) has become the buzz word in the tech industry these days. The meaning of DT can be interpreted in different ways at different places. Put simply, it is the digitization of your business assets with the increased use of technology. If that definition is not simple enough, you can think of an example like moving your physical file/folder based documents to computers and making them accessible instantly rather than browsing through thousands of files stacked in your office. In a large enterprise, this will go to the levels where every asset in the business (from people to vehicles to security cameras) becomes a digital asset and instantly reachable as well as authorized.

Once you have your assets in a digitized format, it is quintessential to expose that digital information to various systems (internal as well as external) through properly managed interfaces. Application Programming Interfaces (APIs) are the de facto standard for exposing your business functionalities to internal and external consumers. It is evident that your DT story will not be completed without having a proper API management platform in place.

Microservices Architecture (MSA) has evolved from being a theory of Martin Fowler's to a go-to technology to implement REST services for your organization when achieving DT. Most developers in the enterprise are moving towards MSA when writing business logic to implement backend core services. But, in reality, there are so many other systems which are coming about as Commercial Off the Shelf (COTS) offerings which do not fit into the microservices landscape natively.

With these basic requirements and unavoidable circumstances within your organization's IT ecosystem, how are you going to implement an efficient API management strategy? This will be the burning problem in most enterprises and I will be touching upon possible solution patterns to address this problem.

## API Management for Green Field MSA

If your organization is just a startup and you don't want to use high-cost COTS software in your IT ecosystem, you can start off with a full MSA. These kinds of organizations are called 'green field ecosystems,' where you have complete control over what needs to be developed and how those services are going to be developed. Once you have your backend core services written as microservices, you can decide whether or not to expose them as APIs through a proper API management platform.

### Pattern 1 - Central API Manager to Manage All Your Microservices

As depicted in the below figure, this design pattern can be applied to a green field MSA where microservice discovery, authentication, and management can be delegated to the central API management layer. There is a message broker for asynchronous inter-service communication.

![MSA central API gateway.png](https://lh5.googleusercontent.com/IFgrmFFRSPnKp9mSt-0m8yDoUJHgX-bFAG4RqoCOaLmbq6eCgbYlLPsPXrXbII7eTuNXxdGhhG0olIpGFl44wJ7c71wu0m89DsEkLOwAyA_vddkb079fgGckjVQ4OqSol2U0necY)

> _Figure 1: Central API management in a green field MSA_

### Pattern 2 - Service Mesh Pattern With Sidecar (Micro Gateway)

This pattern also applies to a green field MSA where all the backend systems are implemented as microservices. But this pattern can also be applied to scenarios where you have both microservices as well as monolithic (COTS) applications with slight modifications.

![MSA micro API gateway \(Service mesh architecture\).png](https://lh5.googleusercontent.com/dFenAOhMaJXsajuBUNfkoOGgJiqDKhvjTe9m9yWcH66gqzfDTC2HeEHzFeQdcACJ2ly5vUAeQf3z62FUxT7pjmEkar37-ftyQS99rfX5RfQgTcwBoDuwrqAzrUj2dEp3oQuwEWfD)

> _Figure 2: API management with service mesh and side car (micro gateway)_

## API Management for Practical Enterprise Architecture

As mentioned at the beginning of this post, most of the real world enterprises use COTS software as well as various cloud services to fulfill their day-to-day business requirements. In such an environment, if you are implementing an MSA, you need to accept that existing systems are there to stay for a long time and MSA should be able to live along with those systems.

### Pattern 3: API Management for Modern Hybrid Ecosystem

This design pattern is mostly suited for enterprises which have COTS systems as well as an MSA. This pattern is easy to implement and has been identified as the common pattern to apply to a hybrid microservices ecosystem.

![Modern enterprise central API gateway with ESB.png](https://lh5.googleusercontent.com/PXPZrySv-QfNIsz55PtF5vewlthXUVliMqfWw3hlbGAO6F88kIxQrAcUwXDazmwfDMe4EI7rPhrvnO9CL-JLGcRCwMSYt1pBuFmVdZ9-CW45ID_85q6WHw0zfdxk2G6k1Jcsm_VY)

> _Figure 3: API management for modern enterprise_

The same pattern can be applied to any enterprise which does not have any microservices but only traditional monolithic applications as backend services. In such scenarios, microservices will be replaced by monolithic web applications.
