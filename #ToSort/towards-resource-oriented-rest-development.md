# Towards Resource-Oriented REST Development

_Captured: 2018-03-08 at 14:06 from [dzone.com](https://dzone.com/articles/towards-resource-oriented-rest-development?edition=366219&utm_source=Zone%20Newsletter&utm_medium=email&utm_campaign=integration%202018-03-08)_

In many areas, we see the use of shared conventions to foster productivity. Docker resp. OCI images start to take over the delivery and installation of server software. Kubernetes seems to be achieving the same for the orchestration of software. Graph databases are leading the way when it comes to modeling and evolving complex, interrelated data sets. In stark contrast, REST development seems to be heading in the opposite direction. Instead of relying on shared conventions, people specify their personal flavor with OpenApi. Developers have to fiddle with path mappings and status codes; maybe with one or the other library offering some short-cuts for common patterns. In contrast, highly efficient, asynchronous frameworks get built that scale to thousands of concurrent requests that only a few of us actually need. This article outlines a number of different possibilities to address these issues, move Java REST development to a higher level, and gain more productivity, consistency, and simplicity.

Ideas to achieve such goals are well established. For example, the [Richardson Maturity Model](https://restfulapi.net/richardson-maturity-model/) specifies four levels of maturity for REST services. Services are supposed to make use of HTTP, have a resource-oriented architecture, perform proper mapping to URLs, and introduce links to facilitate the discovery of the API. Ideally, REST libraries would come with native support for such patterns. Such libraries may make use of three main building blocks in one way or the other:

  * **Resources **that can be inserted, read, updated, and deleted.

  * **Relationships **between resources.

  * **Repositories **to efficiently fetch resources and relationships. This may include sorting, filtering, paging, spare fieldsets, and more.

These are three separate, orthogonal concerns and mixing those concerns can lead to a variety of issues. For example, it is typical for REST libraries to let developers annotate methods with the set of allowed HTTP methods, parameters, and path mappings and then return some data based upon that. This gives developers flexibility. And what could go wrong here? Since it's IT, just about everything. Among other concerns, it makes it very easy and tempting to violate the principles laid out before:

  * Services return data. That data is often a mixture of resources and relationships. But those could be separate concerns, maybe involving different kinds of data stores. 

  * Usually, a model evolves over time and introduces new relationships to existing resources. Maybe the same kind of relationship is used to connect multiple resources. Relationships and resources can make use of different technology stacks. The problems here are not unlike the ones that a graph database addresses, but in the context of APIs instead of data storage.

  * Methods and parameters can get mixed up. Data is held by resources. Leaving the use of parameters to GET requests. As such, parameters should be used to perform efficient data access, such as sorting, filtering, and paging. And such a set of parameters is ideally standardized to facilitate tooling and automation. There is no need for arbitrary parameter usage for most use cases.

  * Path mappings in repositories give absolute freedom to how resources are accessed. But paths should follow a convention and the type of the involved resources should allow one to derive that path. This makes the use of path mappings redundant and unnecessary.

These and other mismatches make REST development inefficient and error-prone, hinder the use of third-party tooling, and complicate the evolution of the application.

What would be interesting, rather, would be to have REST libraries that implement the outlined principles natively and are backed by standards. Aspects like path mappings, linking, structuring of results, sorting, paging, filtering, and more, would be available out-of-the-box. Fortunately, there are a few libraries out there.

### GraphQL

GraphQL is currently one of the more popular APIs out there. A graph is nothing more than resources and relationships. As such, it has a slightly different terminology but fits well with the scope of this article. An application is built with GraphQL by first declaring a model. The model is based on types and fields, for example:

A query then looks like:

And the matching result:

With this, GraphQL moves away from the definition of endpoints towards the definition of types, just like the resource-based architecture outlined before. However, GraphQL also moves away from REST by establishing a query language to request data. One may argue that with this step it also moves away from the simplicity, accessibility, and discoverability that made REST popular in the first place.

### OData

OData can be considered one of the early standards in the area. It is promoted as "SQL for the Web." It has a strong resource-based model. It supports sorting, filtering, and paging. Bulk updates can atomically create, insert, and update resources, something classical REST architectures do not directly address. But in some areas, it may also lack a bit of simplicity. There are smaller things like atypical path mappings:

`GET api/People('russellwhyte')`

rather than:

`GET api/people/`russellwhyte``

Or the exchanged documents make use of property names like

`@odata.context`

Such properties are not easily addressable from languages like JavaScript when processing JSON due to the use of special characters. The application cannot declare interfaces directly but have to introduce mappers or address them through string keys.

### JSON API

[JSON API](http://jsonapi.org/) currently seems to sit in a bit of a sweet spot. The naming one may consider suboptimal as both JSON and API are ubiquitous terms and as such it is easy to mix it up with either of those. But it is a vendor and tool-agnostic standard with many [implementations](http://jsonapi.org/implementations/). It follows the principles of Richardson's Maturity Model with a resource-oriented architecture and HATEOAS. The specification covers:

  * The declaration of resources and relationships.

  * URL conventions.

  * The semantics for POST, GET, PATCH, DELETE methods.

  * Patterns to do sorting, filtering, and paging.

  * How to request a subset of fields for resources.

  * How to request related resources in the same, single request together with the main resources.

  * Validation and error handling of resources.

  * How to attach meta information to data.

  * How to bulk insert, update, and delete resources (as draft scheduled for JSON API 1.1).

In general, JSON API strives for simplicity. The specification is easy to follow. In some areas, only recommendations are given to leave applications the necessary flexibility to go beyond those recommendations. Paging and filtering are two examples of such recommendations. For example, the response to a request for _http://localhost:8080/api/movie/_ taken from [crnk-example](https://github.com/crnk-project/crnk-example/) looks like:

Some noteworthy features are that:

  * Resources are identified by type and id.

  * Data, meta information, link information, and relationships are held separately to make the purpose of a particular element clear; which in turn also facilitates the implementation of libraries on top of JSON API.

  * Response documents are normalized by not nesting resources, but rather including them in an [include section](http://jsonapi.org/format/#fetching-includes). This allows the transmission of arbitrary complex object graphs. And it fits well with newer redux-style applications like [React ](https://reactjs.org/)and [Angular ngrx](https://github.com/ngrx/platform) since the denormalization and normalization step from backend to front-end can be omitted. The normalization further simplifies the update of resources as each resource can be transmitted back separately without having to worry about related resources.

### JSON API With Java

Among [many languages](http://jsonapi.org/implementations/), there are two implementations for Java: [elide ](https://github.com/yahoo/elide)and [crnk](http://www.crnk.io/). Elide closely follows a JPA-related programming model. In doing so, it allows, for example, one to quickly expose JPA entities from Hibernate as JSON API resources. In contrast, crnk is more generic with a core engine and optional modules. The core engine implements the JSON API specification and recommendations. Developers can make use of its API to implement JSON API endpoints to access any kind of data store. It works equally well, for example, with JPA entities, Elastic Search indices, Neo4J graph databases, in-memory datasets, and others. It may also aggregate and interlink multiple such data sources trough JSON API relationships.

On top of the core engine there are numerous integrations into frameworks like JEE and Spring and modules that provide predefined building blocks:

  * Exposing JPA entities as JSON API resources.

  * Exposing Activiti processes, tasks and forms as JSON API resources.

  * Enforcing authorization on resource and fields through the entire system. This includes request documents, filter parameters, sort parameters, requested inclusions, and response documents.

  * Tracing access to repositories with Brave or Spring Sleuth.

The JSON API movie resource example from above is taken from [crnk-example](https://github.com/crnk-project/crnk-example/). It is one example where no custom implementation is necessary. Instead, it is just a JPA entity exposed with [crnk-jpa](http://www.crnk.io/documentation/#_jpa_module) as a JSON API resource:

The endpoint supports the full set of JSON API features. A number of example URLs to play are:

  * http://127.0.0.1:8080/api/movie

  * http://127.0.0.1:8080/api/movie/44cda6d4-1118-3600-9cab-da760bfd678c

  * http://127.0.0.1:8080/api/movie/44cda6d4-1118-3600-9cab-da760bfd678c

  * http://127.0.0.1:8080/api/movie/44cda6d4-1118-3600-9cab-da760bfd678c/project

  * http://127.0.0.1:8080/api/movie/44cda6d4-1118-3600-9cab-da760bfd678c/relationships/project

  * http://127.0.0.1:8080/api/movie?sort=-name

  * http://127.0.0.1:8080/api/movie?sort=-id,name

  * http://127.0.0.1:8080/api/movie?sort=id&page[offset]=0&page[limit]=2

  * http://127.0.0.1:8080/api/movie?filter[name]=Iron Man

  * http://127.0.0.1:8080/api/movie?filter[name][EQ]=Iron Man

  * http://127.0.0.1:8080/api/movie?filter[name][LIKE]=Iron

  * http://localhost:8080/api/movie?include=history

The documentation and example application show a number of further, more advanced use cases like mapping the entities to DTOs or introducing additional, computed attributes based on the JPA ones.

In contrast, a resource that is explicitly implemented with the crnk core API can look like:

It makes use of JSON API specific annotations like `@JsonApiResource` and `@JsonApiRelation`. A repository to provide access to such resources can look as simple as:

Here, data is stored in-memory within a `HashMap`. Sorting, filtering, and paging happen in-memory with `QuerySpec.apply(...)`. From a consumer perspective, it works in almost exactly the same fashion as the earlier JPA-based example. Both follow the JSON API specifications and recommendations. While this example is overly simple, it can still serve two important purposes:

  * Handling data with a low cardinality.

  * Setting up mocks for repositories that are more elaborate to implement or access third-party systems. This allows front-end development to get started quickly with a fully functional backend.

### Connect Data With JSON API Relationships

Both the movie entity and vote resource example have relationships defined. The design and implementation of a relationship can greatly vary depending on the use case:

  * A relationship might be easy to fetch. The vote resource holds it in memory, giving immediate access to it.

  * The id of the related resource might be easy to get, while the entire related resource is expensive to fetch. A typical example is a single-valued JPA relationship where the foreign key is held in the same table as other, more primitive attributes.

  * Both the related id and actual resource are expensive to fetch. The related roles of the earlier movie entity are stored in a separate table that needs to be accessed.

  * A relationship may or may not make use of the same underlying data store as the adjacent resources. It should be possible to connect any kind of data.

  * Consumers may request the complete related resources, the IDs of those resources or neither if not necessary.

In crnk, this translates into two different kinds of implementation strategies:

  * A dedicated relationship repository is implemented to serve all requests for that relationship.

  * One or a combination of both adjacent resource repositories are used to handle relationship requests. Any relationship request is then adapted and forwarded to one of those resource repositories.

The vote resource from earlier is one example of the latter strategy where no relationship repository is necessary. Instead, relationships are directly fetched and updated in memory on the vote resources. All relationship-specific path mappings continue to work, for example:

_http://localhost:8080/api/vote/ffde251b-1a0a-3bbd-9de0-6e08aa7677ec/movie_

The single-valued JPA relationship stored as a foreign key is the second typical example for the latter strategy. Since the relationship is stored in the same table, there is no need to handle it separately. The next example implements a similar use case:

Here the relationship is defined by two attributes: `movie` and `movieId`. `movie`can hold the full resource while `movieId` holds only the ID. The `movieId` can be set and updated by the resource repository. `movie`can remain `null`and the crnk engine will look it up from the opposite resource repository if necessary through the use of `LookupIncludeBehavior.AUTOMATICALLY_WHEN_NULL`. `SerializeType.ONLY_ID` further triggers that `movieId` is always written to the response, regardless of whether the related movie was requested or not. In this example again, there is no need to set up a dedicated relationship repository if the screening resource repository is able to handle updates of `movieId`.

### Interconnecting Different Data Sets

[crnk-example](https://github.com/crnk-project/crnk-example/) introduces a history to each resource to showcase the implementation of a custom relationship repository that works independently of the resource repositories and can connect arbitrary, possibly different, kinds of data stores:

The subsequent `HistoryFieldProvider` introduces a new history relationship for every resource. The historized resource must not even define that relationship, it gets dynamically added:

This is useful for crnk-example as some of its resources are not explicitly defined, but backed by JPA entities. If all resources were to explicitly define that history relationship, this step can also be omitted.

The history elements are then served through`HistoryRelationshipRepository`:

`getMatcher()` specifies that the relationship repository is to be applied to all relationships pointing to History. `findManyTargets(...)` fetches the actual history elements for a given record. [crnk-example](https://github.com/crnk-project/crnk-example/) further implements a `HistoryResourceRepository`to access history elements directly.

### Conclusions

In this article, the benefits of resource-oriented REST architectures have been discussed. The GraphQL, OData, and JSON API standards have been presented that implement such an architecture natively. Resources and relationships are first class citizens here. With [crnk-example](https://github.com/crnk-project/crnk-example/), an example application is shown making use of all these concepts. For more information, you may take a closer look at it and the official [documentation](http://www.crnk.io/documentation/). There is much more to look at. For example, the way resources are secured on resource and attribute levels goes way beyond typical authorization schemes and also covers aspects like sorting and filter parameters.
