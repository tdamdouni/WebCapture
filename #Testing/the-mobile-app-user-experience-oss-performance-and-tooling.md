# The Mobile App User Experience: OSS, Performance, and Tooling

_Captured: 2018-09-13 at 07:07 from [dzone.com](https://dzone.com/articles/the-mobile-app-user-experience-it-all-starts-offli?edition=392202&utm_source=Weekly%20Digest&utm_medium=email&utm_campaign=Weekly%20Digest%202018-09-12)_

Sensu is an open source monitoring event pipeline. [Try it today](https://dzone.com/go?i=299442&u=https%3A%2F%2Fsensu.io%2F%3Futm_source%3DDZone).

Businesses are building more mobile apps than ever before. Their goals? To make operations more efficient, lower costs, and improve customer service.

Mobile workers rely on these apps to get work done, check emails, take notes, speed decision-making, or attend conference calls.

They also demand a rich user experience anytime and anywhere -- even beyond work hours. In fact, a mobile productivity survey of 850 professionals from multiple departments, for Wrike, a collaborative work management platform provider, found that seventy-two percent of people work at [least one to two hours out of the office daily](https://www.wrike.com/blog/released-2016-mobile-productivity-report), and 43 percent claim that mobile devices are critical to getting work done.

They can't always count on their mobile device being connected. However, network coverage can be spotty in some geographical areas and industrial settings. The result can be a lot of lost time and productivity.

## Build Superior Offline Experience

Access to core data and productivity tools -- regardless of connectivity -- is critical to user effectiveness and success.

In a recent report, [Forrester](https://www.forrester.com/report/The+Offline+Mobile+Challenge/-/E-RES117610) observed that "the offline mobile challenge is mobile apps' most important and difficult feature."

Mobile apps should offer similar functionality, such as access to corporate data and a fully rendered UI, whether users are working online or offline. A smooth mobile experience requires an offline-first app development strategy. Specifically, it calls for careful planning, which should include the following:

  * _Analyze the Context_: First, take the time to consider how the app will be used. Identify your organization's goals and the benefits that it's trying to achieve. Is responsiveness important in delivering the best possible experience? Do different groups of users have different mobility needs?
  * _Manage Storage_: Apps should employ a local cache on the mobile device to save data when there is no Internet connection. The UI should be displayed at all times, so users can navigate throughout the app to create, edit, and view documents and files, in both online and offline modes.  
Mobile apps need to load quickly so users can reach all main functions in just a few clicks or steps. This means providing them with the capability of browsing through thousands of records, such as parts catalogs, price lists, or patient records. Large uploads of documents, such as rich files, PDFs, images, and videos, should also be planned carefully. Indeed, the longer it takes to upload, the higher the risk that a connection can be interrupted
  * _Manage Data Synchronizations_: A solid sync framework is crucial for handling data flows and conflict resolution. It should, in particular, let mobile users work on local data when the network is not accessible, syncing it with back-end systems when the network is restored.   
A persistent data structure should ensure seamless data flow between online and offline states. This requires keeping track of newly entered and original values so that both versions can be accessed and modified. You can do this in a number of ways - via custom files, local database, or system-managed repositories
  * _Manage Data Conflicts_: Different versions of data sets on mobile devices and the server can give rise to conflicts. A user, for example, may suddenly go offline and edit a record while another person edits that same record. Rules are needed to minimize the impact these conflicts may have on app performance and user experience.  
This means applying fine-grained controls, such as Read-Only Data, Read/Write Last Write Wins, or Read/Write Data with Conflict Resolution. You can also implement custom algorithms in accordance with the business rules of your specific application.
  * _Manage User Identity_: You need to authenticate users simply and securely to eliminate the risk of employees inadvertently opening, losing, or even maliciously accessing company data.   
Before you can implement policies and controls, you first need to define what information is sensitive, who can access it, and in what circumstances. Then, you can assign privileges to users based on their roles or functions, and securely provision them with information on a need-to-know basis.   
To help with identity and access management, you can also leverage connectors to existing directory services, such as SAML, LDAP, and Active Directory.
  * _Manage Security_: Attackers increasingly use mobile devices to gain access to enterprise networks. That's why security and management controls must be in place to protect data in motion and at rest.   
This requires policies for governing data that moves between the mobile device, the cloud, and your existing enterprise system.  
If your application stores really critical data, it should be encrypted both on the network and the mobile device. You can leverage encryption technologies, such as resolution AES 256. Mobile SDKs can also provide you with the necessary toolbox for encrypting and decrypting data from local databases

## Tools of the Trade

Writing this complex networking logic manually can be time-consuming. In fact, developing mobile app offline capabilities can typically represent up to 90 percent of development time and effort.

Of course, in-browser databases, such as [PouchDB ](https://pouchdb.com/)or Google's [Firebase](https://firebase.google.com/docs/database/), can help solve technical issues. They let apps save data locally and sync it with anything that implements the Couch DB replication protocol. Pouch DB, for example, allows users to read and write data directly on the device, and then syncs this data back to the cloud when they have an internet connection.

But, managing many distinct components and low-level tools, however, can be complex and time-consuming. You can end up spending more time and resources than you want on development, maintenance, testing, and integration efforts.

## Scale Up to a Mobility Platform

Full-stack Mobile Application Development Platforms (MADPs/ MBaaS) are a more robust solution that can ease the burden of integrating multiple technologies.

MADPs' cohesive architecture helps developers build, test, deploy, host, and maintain mobile apps throughout the entire lifecycle. As a result, your apps can scale more easily as your organization changes and grows.

MADPs consolidate front- and back-end functionality. Building block services are provided, such as user management, data management, and push notifications. You can reuse these services rapidly and share with others. MADPs also automate the building of offline-first functionality, such as connecting to back-end systems of record and offering more sophisticated data synchronization mechanisms. Pre-made connectors to APIs and third-party infrastructure, such as SAP, Oracle, Salesforce, SQL Web Service, also make it easy to interface with multiple databases in a bi-directional way.

In the end, a full-stack MADP's architecture can reduce delays and cost and provide better service at every stage in the app lifecycle. This will help you deliver mobile apps that are also more scalable and extensible.

## Consider Open Source

Open source software can be defined as "software with source code that anyone can inspect, modify, and enhance."

An open source MADP, in particular, is developed by a community. You can use it and modify it freely to meet your specific needs.

Open source communities adhere to open standards around communication protocols and data formats. The result is the easy integration of new solutions and a higher level of interoperability for business and customer applications. A case in point is [Convertigo](https://www.convertigo.com/), the first software vendor to provide a MADP and MBaaS -- both cloud-based and on-premise -- that is based on the open source model. This scalable and secure MADP integrates rapid cross-mobile development tools and a powerful Mobile Back-end-as-a-Service (MBaaS) solution.

Because the code is public, open source allows for easy integration of new solutions, so IT professionals can improve legacy infrastructure more efficiently than by working with many proprietary solutions vendors.

## Performance Is Key

Today's mobile workers expect anytime, anywhere access to their corporate apps and data. Speed in delivering the best possible experience is essential. These apps should also remain responsive through poor and intermittent connections, or when servers are overloaded and responding poorly.

Offline capabilities are at the core of being successful in this effort. This calls for applying an offline-first development philosophy and writing apps to be used as if they had no Internet connection. The use of a full-stack MADP platform will greatly facilitate this offline app development approach and provide the foundation you need to empower your mobile workforce.

Sensu: workflow automation for monitoring. [Learn more--download the whitepaper.](https://dzone.com/go?i=302541&u=https%3A%2F%2Fmonitoringlove.sensu.io%2Fmonitoringeventpipeline%3Futm_source%3DDZone)

Topics:

mobile app development. ,enterprise app development ,mbaas ,madp ,low code development ,microservice ,offline ,devops ,open source
