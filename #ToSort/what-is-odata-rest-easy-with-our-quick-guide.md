# What is OData? REST Easy with Our Quick Guide

_Captured: 2017-02-09 at 14:20 from [www.progress.com](https://www.progress.com/blogs/what-is-odata-rest-easy-with-our-quick-guide)_

![What is OData REST Easy with Our Quick Guide_870x220](https://d117h1jjiq768j.cloudfront.net/images/default-source/blogs/2016-11/what-is-odata-rest-easy-with-our-quick-guide_870x220.jpg?sfvrsn=2)

OData, or "SQL for the Web"--what is it? Do you need it? Here is a comprehensive guide to OData to help you answer these questions.

OData is a REST-based protocol for querying and updating data. It is built on technologies like HTTP, ATOM/XML and JSON. It is more flexible than other REST-based web services and provides a uniform way to describe the data and the data model for easy interoperability between data sources, applications, services and clients. Similar to ODBC and JDBC, OData gives you a single way of accessing various data sources.

Consumers of OData master one API and use it to consume multiple data sources. As a producer, OData relieves you from spending your resources to defining and maintaining data access and discovery API. [OData is an OASIS standard](https://www.oasis-open.org/news/pr/oasis-approves-odata-4-0-standards-for-an-open-programmable-web) and is [beginning the standardization process with ISO](https://www.oasis-open.org/news/announcements/member-review-of-proposed-submission-of-odata-v4-0-and-odata-json-format-v4-0-to-). It defines the best practice for building and consuming RESTful APIs.

![OData](https://d117h1jjiq768j.cloudfront.net/images/default-source/default-album/odata19b0a646ebc0454a83a348862e99beb3.gif?sfvrsn=0)

## Why Use OData?

With the vast amount of data from web browsers, mobile apps and business intelligence tools, how could you possibly combine all of this disparate data and make use of it in applications? The monumental task of crafting unique code for every different data source to create a unified, robust application discourages organizations from approaching serious application development.

What OData does is take this interconnected ecosystem of data from all these disparate sources and builds upon existing web standards to facilitate simple, high caliber data connectivity. These standards enable greater efficiency than ever before in everything from custom applications, to cloud storage, to content management.

The best part about OData is that it is basically a standardized REST interface. So, when you think OData, you should also think REST/JSON. This enables you to use the OData standards with any RESTful interface--whether you are programming in Android, iOS, Salesforce Connect or other similar interfaces.

## Dissecting OData Technology

Feeds (collections of typed entries) are at the center of OData. Every entry is represented by a structured record with a key that holds a list of properties of both primitive and complex types. Entries can be part of a hierarchy and can also have related entries and related feeds through links. OData services also have the ability to expose Service Operations (simple, service-specific functions that accept input parameters and return entries or complex/primitive values).

In order to find the shape of an OData Service along with its structure, known links and service operations, OData services also expose a Service Metadata Document. These documents describe a given service's Entity Data Model (the underlying abstract data model used by OData services to formalize the description of the resources it exposes).

![OData_Clients_DataSources](https://d117h1jjiq768j.cloudfront.net/images/default-source/blogs/2016-11/odata_clients_datasources.png?sfvrsn=0)

## Four Fundamentals of OData

In its most basic form, the OData model is fundamentally broken down into four different pieces:

  1. **The OData Data Model**--The OData Data Model is a server-side model, meaning that the data set is only available on the server and the client only knows the currently visible (requested) data. Operations, such as sorting and filtering, are done on the server. The client sends a request to the server and shows the returned data. 

Another key aspect of the model is an OData metadata document. They describe the Entity Data Model (EDM) for a given service, which is the underlying abstract data model used by OData services to formalize the description of the resources it exposes.

  2. **The OData Protocol**--This enables clients to make requests and retrieve responses from an OData service. This includes CRUD operations and OData defined query language. An OData service can be represented in XML-based format defined by Atom/AtomPub or in JSON.
  3. **OData Client Libraries**--[OData libraries](http://www.odata.org/libraries/) enable you to quickly and easily access and produce OData APIs. They exist for all kinds of interfaces including .NET, Java, C++, JavaScript, Python, Objective C, iOS and more.
  4. **An OData Service**--Simple OData services may consist of just a feed. More sophisticated services can have several feeds, and in that case it is useful to expose a service document that lists all the top-level feeds so clients can discover them and find out the addresses of each of them. For example, this URI, http://services.odata.org/OData/OData.svc, identifies the service document for a sample OData service.

To fully understand OData and practice these concepts on your own in C#, Olingo JavaScript client, C++ or Node.js, or if you want to contribute to OData as an Open Source project, we advise you try OData.org's interactive tutorial, [Understand OData in 6 Steps](http://www.odata.org/getting-started/understand-odata-in-6-steps/).

## Our Personal OData Story

OData, originally started by Microsoft in 2007, began to grow until the Microsoft team realized that for the standard to be fully embraced, it would need to move to Open Group (Open Standards Organization). Following this move, Microsoft approached our team at Progress DataDirect (known as the Switzerland of data access) to cosign the project. We believe in a future of open standards and writing them in such a way as to apply to as many data sources as possible.

We care about standards like OData, JDBC and ODBC and take part in their development and innovation because this is how we make the highest quality data connectivity products in the industry. We connect any data source to any application via OData, JDBC or ODBC.

## Start Using OData

The OData standard is powerful. From producers to consumers, it offers tremendous benefits. Knowing this, what are your next steps? How do you expose your data as OData or consume it? That's where both DataDirect Cloud and our newest solution, Hybrid Data Pipeline, become your best friend.

### DataDirect Cloud

[DataDirect Cloud](https://www.progress.com/cloud-data-integration) accepts OData query requests, translates the query to SQL, and then forwards the SQL to the backend data source to be executed. Applications can invoke the DataDirect Cloud OData service endpoints using any of the common clients that provide HTTP or web service access. This solution is hosted by Progress DataDirect servers.

Learn [how to get started](https://www.progress.com/blogs/getting-started-with-odata) with OData and DataDirect Cloud.

### Hybrid Data Pipeline

[Hybrid Data Pipeline](https://www.progress.com/hybrid-data-integration) is the industry's first lightweight, embeddable hybrid data access service. DataDirect Hybrid Data Pipeline will "disrupt the disruption" of cloud applications by providing direct SQL (ODBC or JDBC) or REST (OData) standards-based data access for hybrid cloud and on-premises architectures, completely changing the way cloud applications access external data. This solution is incredibly flexible and is hosted on your own servers.

You can learn more about Hybrid Data Pipeline in the video below--and don't forget to [register](https://www.progress.com/campaigns/datadirect/webinars/new-data-pipeline-transforms-how-clouds-access-data-oem-gen?SFDCID=701a00000027inR&utm_source=progress&utm_medium=blog&utm_campaign=Hybrid-Data-Pipeline-OEM-Gen-webinar-Nov2016) for our [webinar on the topic](https://www.progress.com/blogs/webinar-new-data-pipeline-transforms-how-clouds-access-data) tomorrow.

[Explore Hybrid Data Pipeline](https://www.progress.com/blogs/webinar-new-data-pipeline-transforms-how-clouds-access-data)
