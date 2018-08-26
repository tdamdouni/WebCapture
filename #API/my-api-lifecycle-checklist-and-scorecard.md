# My API Lifecycle Checklist and Scorecard

_Captured: 2018-07-26 at 17:51 from [dzone.com](https://dzone.com/articles/my-api-lifecycle-checklist-and-scorecard?edition=385289&utm_source=Zone%20Newsletter&utm_medium=email&utm_campaign=integration%202018-07-26)_

**[The State of API Integration 2018](https://dzone.com/go?i=285436&u=https%3A%2F%2Foffers.cloud-elements.com%2Fthe-state-of-api-integrations-report-2018%3Futm_source%3Ddzone%26utm_medium%3Ddisplay%26utm_content%3Dpre-roll): Get Cloud Elements' report for the most comprehensive breakdown of the API integration industry's past, present, and future.**

I am working on delivering a handful of new APIs, which I will be turning into products. I will be prototyping, developing, and operating them in production environments for myself, and for a handful of customers. To help guide my workflow, I've crafted this API lifecycle definition to help direct my efforts in an ongoing lifecycle approach.

**Define** -- Define the problem and solution in a human and machine-readable way.

  * **Repository** -- Establish a Github repository.
  * **README** -- Craft a README for the repository.
  * **Title** -- Provide title for the service.
  * **Description** -- Provide concise description for the service.
  * **Goals** -- Establish goals for the service.
  * **Schema** -- Organize loose, and JSON schema for the service.
  * **OpenAPI** -- Establish an OpenAPI for the service.
  * **Assertions** -- Craft a set of assertions for the service.
  * **Team** -- Define the team behind the service.

**Design** -- Establish a base set of design practices for the service.

  * **Versioning** -- Determine how the code, schema, and the API be versioned.
  * **Base Path** -- Set the base path for the service.
  * **Path(s)** -- Define a set of resource paths for the service.
  * **Verb(s)** -- Define which HTTP and other verbs will be used for the service.
  * **Parameters** -- Define a list of query parameters in use to work with service.
  * **Headers** -- Define the HTTP Headers that will be used to work with the service.
  * **Response(s)** -- Provide a resulting message and associated schema definition for the service.
  * **Media Types** -- Define whether service will return CSV, JSON, and / or XML responses.
  * **Status Codes** -- Define the available status code for each response.
  * **Pagination** -- Define how pagination will be handled for requests and responses.
  * **Sorting** -- Define how sorting will be handled for requests and responses.

**Database** -- Establish the base for how data will be managed behind the service.

  * **Platform** -- Define which platform is in use to manage the database.
  * **Schema** -- Establish the schema used for database based upon definition provided.
  * **Location** -- Define where the database is located that supports services.
  * **Logs** -- Define where the database logs are located that support services.
  * **Backup** -- Define the database backup process and location for service.
  * **Encryption** -- Define the encryption layer for the service database.

**Storage** -- Establish how all objects will be stored for the service.

  * **Platform** -- Define which platform is used to store objects.
  * **Location** -- Define where objects are stored behind the service.
  * **Access** -- Quantify how objects access is provided behind the service.
  * **Backup** -- Define the backup process for objects behind the service.
  * **Encryption** -- Define the encryption layer for stored objects.

**DNS** -- Establish the DNS layer for this service.

  * **Platform** -- Define which platform is used to operate DNS.
  * **Prototype** -- Provide host for prototype of service.
  * **Mock** -- Provide host for mock of service.
  * **Development** -- Provide host for development version of service.
  * **Production** -- Provide host for production version of service.
  * **Portal** -- Provide host for the portal for this service.
  * **Encryption** -- Define the encryption layer for service in transport.

**Mocking** -- Provide a mock representation of this service.

  * **Paths** -- Providing virtualized paths for the API driving service.
  * **Data** -- Providing synthesized data behind each API response for service.

**Deployment** -- Define the deployment scaffolding for this service.

  * **Platform** -- Define the platform used to deploy this service.
  * **Framework** -- Define the code framework used to deploy service.
  * **Gateway** -- Define the gateway used to deploy service.
  * **Function** -- Define the function(s) used to deploy service.
  * **Containers** -- Define the container used to deploy service.
  * **Pipeline** -- Define the pipeline in place to build and deploys service.
  * **Location** -- Define where the service is deployed to.

**Orchestration** -- Define how the service will be orchestrated.

  * **Build** -- Define the build process for this service.
  * **Hooks** -- Detail the pre and post-commit hooks in use for this service.
  * **Jobs** -- Define the jobs being executed as part of this service operations.
  * **Events** -- Define the events that are in play to help operate this service.
  * **Schedule** -- Details of the schedules used to orchestrate this service.

**Dependencies** -- Providing details of the dependencies that exist for this service.

  * **Service** -- Details of other services this service depends upon.
  * **Software** -- Details of other software this service depends upon.
  * **People** -- Details of other people this service depends upon.

**Authentication** -- Details regarding authentication in use for this service.

  * **Type** -- Define whether this service uses Basic Auth, API Keys, JWT, or OAuth for authentication.
  * **Overview** -- Provide a location of the page that delivers an overview of this services authentication.

**Management** -- Define the management layer for this service's API.

  * **Platform** -- Defining the platform used for the API management layer.
  * **Administration** -- Provide a location for administrating the management layer.
  * **Signup** -- Provide a location for users to signup for access to this service.
  * **Login** -- Provide a location for users to log in to access to this service.
  * **Account** -- Provide a location for users to access a dashboard for this service.
  * **Applications** -- Provide the location of applications that are approved to use service.

**Logging** -- Define the logging layer for supporting this service.

  * **Database** -- Define the logging for the database layer.
  * **API** -- Define the logging for the API access layer.
  * **DNS** -- Define the logging for the DNS layer.
  * **Shipping** -- Define how longs are shipped or centralized for auditing.

**Monetization** -- Define the costs associated with the delivery of this service.

  * **Acquisition** -- Provide costs associated with the acquisition of resources behind service.
  * **Development** -- Provide costs associated with the development of this service.
  * **Operation** -- Provide costs associated with the operation of this service.
  * **Value** -- Provide a description of the value delivered by this service.

**Plans** -- Define the operational plan for the business of this service.

  * **Tiers** -- Define the tiers of access in place to support this service.
  * **Elements** -- Define the elements of access for each tier for this service.
  * **Paths** -- Define which API paths are available as part of each tier or service.
  * **Metrics** -- Provide a list of metrics being used to measure service access.
  * **Timeframes** -- Define the timeframes in use to measure access to this service.
  * **Limits** -- Define what limitations and constraints are in place for this service.
  * **Pricing** -- Define the monetary value in place to define the price for this service.

**Portal** -- Define the public or private portal in use to present this service.

  * **Hosting** -- Provide details on where this service portal is hosted.
  * **Template** -- Define which graphical UI and brand template is in use for this portal.
  * **Analytics** -- Define which analytics package is used to measure traffic for the portal.

**Documentation** -- Provide documentation for this service within the portal.

  * **Overview** -- Publish concise over for this service's documentation.
  * **Paths** -- Publish an interactive list of API paths available for service.
  * **Examples** -- Provide as many examples of API requests in a variety of languages.
  * **Definitions** -- Publish a list of schema definitions in use by this service.
  * **Errors** -- Provide a list of available errors users will encounter for this service.

**Getting Started** -- Provide a getting started page for this service within the portal.

  * **Overview** -- Provide an introduction to the getting started process for this service.
  * **Signup** -- Provide a link to where users can signup for this service.
  * **Authentication** -- Provide a link to the authentication overview for this service.
  * **Documentation** -- Provide a link to the documentation for this service.
  * **SDKs** -- Provide a link to where users can find SDKs and code libraries for this service.
  * **FAQ** -- Provide a link to to the frequently asked questions for this service.
  * **Support** -- Provide a link to where users can get support for this service.

**SDKs** -- Providing code samples, libraries, or complete software development kits (SDKs).

  * **PHP** -- Provide a PHP SDK.
  * **Python** -- Provide a Python SDK.
  * **Ruby** -- Provide a Ruby SDK.
  * **Go** -- Provide a Go SDK.
  * **Java** -- Provide a Java SDK.
  * **C#** -- Provide a C# SDK.
  * **Node.js** -- Provide a Node.js SDK.
  * **JavaScript** -- Provide a JavaScript SDK.

**FAQ** -- Publish a list of the frequently asked questions (FAQ) for this service.

  * **Categories** -- Break all questions down by logical categories.
  * **Questions** -- Publish a list of questions with answers within each category.
  * **Ask Question** -- Provide a form for users to ask a new question.

**Roadmap** -- Provide a roadmap for the future of this service.

  * **Private** -- Publish a private, internal version of entries for the roadmap.
  * **Public** -- Publish a publicly available version of entries for the roadmap.
  * **Suggest** -- Provide a mechanism for users to make suggestions for the roadmap.

**Issues** -- Provide a list of currently known issues for this service.

  * **Entries** -- Publish a list of all known issues currently outstanding.
  * **Report** -- Provide a mechanism for users to report issues.

**Change Log** -- Providing a historical list of what has changed for this service.

  * **Outline** -- Publish a list of all roadmap and issue entries that have been satisfied for this service.

**Communication** -- Establish a communication strategy for this service.

  * **Blog** -- Provide a simple blog and update mechanism for this service.
  * **Twitter** -- Provide the Twitter handle that is used as part of this service.
  * **Github** -- Provide the Github account or organization behind this service.
  * **Internal** -- Provide a location where internal communication is available.
  * **External** -- Provide a location where public communication is available.

**Support** -- Establish the support apparatus in place for this service.

  * **Email** -- Define the email account used to support this service.
  * **Issues** -- Provide a URL to the repository issues to support this service.
  * **Tickets** -- Provide a URL to the ticketing system used to support this service.

**Licensing** -- Provide a set of licensing in place for this service.

  * **Server** -- Define how all backend server code is licensed for this service.
  * **Data** -- Define how all data and schema is licensed for this service.
  * **API** -- Define how the API definition is licensed for this service.
  * **SDK** -- Define how all client code is licensed for this service.

**Legal** -- Provide a set of legal documents guiding the service.

  * **Terms of Service** -- Provide terms of service for this service to operate within.
  * **Privacy Policy** -- Provide a privacy policy for this service to operate within.
  * **Service Level Agreement** -- Provide a service level agreement (SLA) for this service to operate within.

**Monitoring** -- Defining the uptime monitoring for this service.

  * **Monitors** -- Establish the monitors for this service.
  * **Status** -- Provide real-time details of monitor activity.

**Testing** -- Defining the testing for this service.

  * **Assertions** -- Provide details of the assertions being tested for.
  * **Results** -- Provide real-time details of testing activity.

**Performance** -- Defining the performance monitoring for this service.

  * **Tests** -- Provide details of the performance testing in place for this service.
  * **Results** -- Provide real-time details of performance testing activity.

**Security** -- Defining the security practices in place for this service.

  * **Overview** -- Provide the URL of the security practices overview page.
  * **Policies** -- Define the security, IAM, and other policies are in place for this service.
  * **Tests** -- Define the security tests that are conducted for this service.
  * **Results** -- Provide real-time details of security testing activity.

**Discovery** -- Defining the discovery aspects for this service.

  * **API Discovery** -- Publish an API Discovery (APIs.json) index for the project.
  * **OpenAPI** -- Provide URL for all OpenAPI definitions and index in API discovery index.
  * **Postman Collection** -- Provide URL for all Postman Collections and index in API discovery index.

**Analysis** -- Define the analysis in play for this service.

  * **Traffic** -- Document traffic to the service portal.
  * **Usage** -- Document usage of APIs for the service.
  * **Activity** -- Document other activity around the service.
  * **SLA** -- Document whether the SLA was met for this service.

**Stages** -- Define the stages that are applied to this lifecycle outline.

  * **Prototype** -- When a prototype of this service is being developed.
  * **Development** -- When a production instance of service is being developed.
  * **Production** -- When a production instance of service is being operated.

**Maintenance** -- Define the maintenance cycles applied to this lifecycle outline.

  * **Daily** -- Provide a version of this outline that should be considered daily.
  * **Weekly** -- Provide a version of this outline that should be considered weekly.
  * **Monthly** -- Provide a version of this outline that should be considered monthly.
  * **Releases** -- Provide a version of this outline that should be considered for each release.
  * **Governance** -- Provide an outline of how this outline is measured, reported, and evolved.

This outline gets executed differently depending on the service stage and maintenance cycle being executed. It is meant to provide a master checklist to consider from day one, and every other time this service is being versioned, maintained, and considered as part of my overall operations. Providing a living checklist, and scorecard rubric for how well this service is doing, depending on stage and maintenance dimensions.

Ultimately the API Discovery (APIs.json) document is the heartbeat for this service checklist, which resides in the root of the GitHub repository will provide the machine-readable index for reporting and governance, while also driving the human-readable interface that is accessible via the service portal, which is driven by Jekyll running in GitHub Pages. That is something I will publish more about next, as part of a working portal for one of the first services coming off the assembly line.

Your API is not enough. Learn why (and how) leading SaaS providers are turning their products into platforms with API integration in the ebook, [Build Platforms, Not Products](https://dzone.com/go?i=263426&u=https%3A%2F%2Foffers.cloud-elements.com%2Fbuild-platforms-not-products-ebook%3Futm_campaign%3DPlaforms%25252C%252520Not%252520Products%252520eBook%26utm_source%3Ddzone%26utm_medium%3Ddisplay%26utm_content%3Dtext) from Cloud Elements.
