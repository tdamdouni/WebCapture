# RESTful SNMP Over HTTP: Part I

_Captured: 2017-03-20 at 14:36 from [dzone.com](https://dzone.com/articles/restful-snmp-over-http?edition=285896&utm_source=Daily%20Digest&utm_medium=email&utm_campaign=dd%202017-03-19)_

Welcome to Part I of a series attempting to map the good ol' SNMP protocol into something more modern and API-friendly following RESTful logic. In this first post, we'll see the basics of this mapping -- starting with OIDs and SNMP objects.

## Technical Problem

The problem is finding a way to publish the internal MIB (Management Information Base) data structure of a network device in a safe and uniform way through a more commonly available protocol as HTTP(S) (HyperText Transfer Protocol [Secure]).

Furthermore, the goal is letting both human and software agents use those data through the same criteria, with the same operations done in the same way, possibly without the need for customized or specific software. This will also solve another problem; SNMP (Simple Network Management Protocol) usually needs firewall customizations and adaptations while HTTP(S) TCP (Transmission Control Protocol) ports are usually open and available.

## State of the Art

Network devices generally propose two or three different kinds of interfaces.

  1. The first and most common is the **SNMP interface**, which is generally open to third-party software and specific applications such as MIB browsers.

  2. The second one is commonly a **web application** that hides internal mechanisms and data while providing the (human) user the possibility to act on the devices.

  3. The third solution, if available, is a **device-customized software** (desktop- or web-based) that provides finer grain controls on the device itself, usually through SNMP or HTTP requests.

All these interfaces have different behaviors and content presentations according to users' needs. SNMP is the classic and low-level, with no GUI (Graphical User Interface), but with the possibility to interact easily via MIB browsers software applications using widespread APIs (Application Programming Interface) or tools.

The (web- or desktop-based) GUIs provide more high-level contents but are usually unusable by automated software applications that want to be interacting with such elements. Some solutions provide (usually limited) SOAP (Simple Object Access Protocol) messages that can query web services through software (and usually XML messages) custom-made according to provided WSDL (Web Services Description Language) descriptions.

All these solutions do provide some interactions with devices, but they do not have a uniform interface and management. In addition, developers must build software strictly following the provided WSDL specification for each web service they need if they want to use such service. Again, human and software interactions have different logical levels and different content provided for each agent.

A possible solution to this problem is represented by RFC 4088 that maps SNMP to URI using an URI scheme like this:

...providing it as a path for the SNMP objects that has to be identified, aiming at the literal use of the URI acronym meaning. This RFC designates such a valid URI scheme for SNMP protocol in order to allow external identification of the SNMP objects without all considerations for SNMP operations such as `Trap` or `InformRequest`. Also, it does not describe the possible output formats in reply to this URI or a possible way to send data for `SetRequest` SNMP operations.

![Picture taken from RFC 4088](https://dzone.com/storage/temp/4517904-rfc4088.png)

> _Picture taken from RFC 4088_

Another possible solution presents a software gateway between SNMP and XML. This solution too is limited, since it does not leverage HTTP protocol features, limiting its functionalities as a simple gateway to actual SNMP requests. Moreover, SOAP/XML (eXtensible Markup Language) messages through `HTTP`, `GET`, and `POST` methods only mediate the transport of information between user and SNMP, leaving the hard work of translating and interpreting these data to a web application.

![Picture taken from cited article](https://dzone.com/storage/temp/4517937-figure4.png)

> _Picture taken from cited article_

## Basic Idea

The idea described in this document depicts a method to map MIB concepts and OIDs (Object Identifiers), and to structure together with the general SNMP operations through a list of URIs (Uniform Resource Identifier) with associated HTTP(S) operations in a uniform way. This provides input and output possibilities for both user and software agents in the same way.

This idea is neither a software gateway nor a proxy implementation between SNMP and HTTP or an HTTP/XML/SOAP medium between the user and the SNMP. It is actually a logical mapping between SNMP/MIB and HTTP/URIs concepts. The idea is an HTTP RESTful view of the same SNMP MIB data structure so that users can interact with such data structure using both SNMP and this RESTful HTTP interface.

This idea maps the MIB objects and their OIDs on HTTP URIs and SNMP-like operations to HTTP methods so that it is even possible to fully remove SNMP.

Both SNMP and HTTP are stateless protocols that generally do not have session concepts. They both provide read and write operations on data, describing requests and responses structures in the proper way, whereas SNMP usually requires specific software (i.e., MIB browser or custom software), HTTP can be managed by all common Internet browsers and even simpler tools like [WGet ](https://en.wikipedia.org/wiki/cURL)or [cURL](https://en.wikipedia.org/wiki/Wget) .

[REST (Representational State Transfer) guidelines](http://www.ics.uci.edu/~fielding/pubs/dissertation/rest_arch_style.htm) are the basics on which this idea builds a mapping and where more strict RESTful concepts such as ROA (Resource-Oriented Architecture) are referred to provide a real uniform layout to the MIB/SNMP mapping towards HTTP and URIs.

Applying RESTful concepts and HTTP protocol methods (`GET`, `HEAD`, `GET`, `PUT` , `DELETE`, `TRACE`, `OPTIONS`, `CONNECT`, `PATCH`), the user will be able to `GET` resources details, `DELETE` resources on the network element, `PUT` new resources in the network element, etc.

Since REST defines scalable concepts and mechanisms, this solution may easily provide more human-user-friendly content when operated by a human user, while at the same time providing more structured and well-defined content (for the same resource) when operated by a software agent.

This idea applies the so-called [Richardson Maturity Model for REST](http://martinfowler.com/articles/richardsonMaturityModel.html) and the [hypermedia concepts by Roy Fielding](http://roy.gbiv.com/untangled/2008/rest-apis-must-be-hypertext-driven) to the SNMP protocol, deriving an HTTP(S) version of the same.

Beginning with protocols standards and the definition of REST(ful), the solution applies REST concepts to SNMP/MIB. It's proposing a set of deterministic rules that map MIB hierarchy and SNMP operations to HTTP requests and responses, allowing interaction with a generic MIB through a RESTful HTTP interface.

Many tools can interact with such interface: simple command line applications such as cURL or WGet are more than enough to operate. Nevertheless, there are also general-purpose REST(ful) clients already available such as the [REST Client plugin for IntelliJ IDEA](http://plugins.jetbrains.com/plugin/?idea&id=2200), the [REST HTML 5 Client plug-in for NetBeans IDE](http://restclient.net/), the [RESTClient plugin for Mozilla Firefox](http://restclient.net/), and so on. Other APIs such as [Ruby's rest-open-uri gem](https://rubyforge.org/projects/rest-open-uri/) may help.

## OID Mapping Rule

The base of this idea is the following mapping rule: The MIB OID of any object will become a URI for such a resource, and using indexes and table fields, it is possible for further filtering the HTTP requests -- just as SNMP allows doing. With these URIs, HTTP methods encode SNMP-like requests, with some care on HTTP requests and responses header fields' usage.

The idea also presents a way to build URI that translates the classical dotted way to write OIDs (such as 1.3.6.1.2.1.118) into a hierarchical slashed (and more URI/HTTP-oriented) way to write them (such as `1/3/6/1/2/1/118`).

The traditional dotted notation for OID can possibly be used as a more user-friendly alternative for easier OID copying and pasting: `URI_ROOT/1.3.6.1.2.1.118.1.1.2/`. Even though this format is less likely URI/hierarchical-oriented, it will help users by increasing the interaction with all other SNMP/MIB-specific tools that use the classical dotted notation for MIB entries.

This idea anyway will refer below to the slashed URI/HTTP-oriented notation, noting that the more classical 'dotted' notation can be used as well.

The solution defines this way to map SNMP/MIB objects to RESTful resources: a generic URI is structured according to the generic scheme:

`http[s]://[user[:password]@]network.element.ip.address[:port]/{resource}/`.

Following common URIs usage, having the username and password for both HTTP and HTTPS is not mandatory. To highlight all these possibilities in the scheme URI above I have used common conventions with square brackets `[]` for optional parameters and curly braces `{}` for mandatory parameters.

I prefer to replace the long basic URI scheme described above as `http[s]://[user[:password]@]network.element.ip.address[:port]/{resource}/` with the simpler string `URI_ROOT/{resource}/`.

This idea and mapping rule works regardless the use of IPv4 or IPv6 addresses: for the standard definition of URI see [Internet standard 66](http://tools.ietf.org/html/std66), [RFC 3986](http://datatracker.ietf.org/doc/rfc3986/), and [updated RFC 6874](http://datatracker.ietf.org/doc/rfc6874/).

In the schemes above, `{resource}` is the slashed OID of a specific MIB object.

Example: In Alarm MIB root (OID: 1.3.6.1.2.1.118), the `AlarmModelTable` object has the OID 1.3.6.1.2.1.118.1.1.2. This will be directly mapped to: `URI_ROOT/1/3/6/1/2/1/118/1/1/2` and the corresponding naming convention may also be used.

OID 1.3.6.1.2.1.118.1.1.2 translates to: and even mixed format such as...

...may be allowed, according to actual implementations. With this definition only, through the HTTP protocol `GET` method, each and every MIB object can be easily retrieved for read-only purposes, both in plain (HTTP) and secure (HTTPS) modes.

As said, the traditional SNMP dotted notation may be used, as well, both for OID and named (or even mixed) URIs.

If there would be the need to still emulate SNMP-like behavior, the user part of the URI scheme above can be used to specify the community string from SNMPv2c draft (but de facto) standard. The scheme, still general, may so be specified as `http[s]://[communityString@]network.element.ip.address[:port]/{resource}`.

## Indexing and Filtering Rules

In order to add more functionality and possibly filter the requested columns of tabular objects, this idea and solution foresees (again) the use of URIs: post-fixing the ordered list of required column(s) to a URI, together with the possibility to define a convention for strictly ordered requests or even unordered requests, allows detailed filtering.

It is possible to customize the URIs in this way: `URI_ROOT/{resource}/column1,column2,column5` with the commas (`,`) separating columns' names in the desired order. For the sample MIB table above, the URI-defined `URI_ROOT/{resource}/alarmListName,filtering,alarmModelState` describes the possible set of desired columns to filter/select in the request, and so on.

In this way, it is possible to request each column of each table independently from the whole table, specifying the desired order. The use of semicolons (`;`) instead of commas can provide the same list of columns, but no specific order shall be considered in received data. This can be useful when data have not a specific order or the order is not meaningful.

Still, for tabular objects, this indexing shall provide the whole set of rows of the table. It is then necessary to enhance the URI in the case of a need for filtering to provide detailed needs such as limiting the provided set of rows.

For example, the triplet `alarmListName`, `alarmModelIndex`, and `alarmModelState` indexes the `alarmModelTable` described above.

Following this, the filtering part of the URI can be easily identified.`URI_ROOT/{resource}/a_name/1342/1` identifies the alarm belonging to the list `a_name`, indexed by number `1342`, and cleared (`1`).

A further customization can be useful with fine-grained and advanced implementations: placing wildcard characters (`*`) in indexes to skip the filtering according to that index. For example, `URI_ROOT/{resource}/a_name/*/1` may represent the same request as above, but for all index numbers.

Preparing the URI without those indexes automatic filters on outer indices (i.e., to require all alarms for the `a_name` list, the URI is `URI_ROOT/{resource}/a_name/` that may be reasonably considered identical in behaviour to `URI_ROOT/{resource}/a_name/*/*`.

Therefore, summarizing OIDs, immediately identify the scalar object (without the need for the final `.0`) as REST resources with the `BASIC_URI` definition below. For each tabular object, instead, the `BASIC_URI` may be further specified in order to properly identify and filter table contents:

  * **URI_ROOT = `http[s]://[username[:password]@]ne.ip.address`**

    * Example: `http://151.98.96.118`

    * URI_ROOT = `http[s]://[username[:password]@]ne.dns.name`

    * Example: `http://user@example.com`

  * **BASIC_URI = URI_ROOT + `/whole/OID/for/the/resource`**

    * Example: `https://example.com/1/3/6/1/2/1/118/1/2/2`

    * Example: `https://example.com/1.3.6.1.2.1.118.1.2.2`

    * Named example: `https://example.com/iso/org/dod/internet/mgmt/mib/alarmMIB/alarmObjects/alarmActive/alarmActiveTable`

  * **INDEXED_URI = BASIC_URI + [`/ordered/index/data`]**

    * Example: `http://example.com/1/3/6/1/2/1/118/1/1/2/a_name/1342/1`

      * Note: This INDEXED_URI scheme may use wildcard characters (`*`), replacing one or more indices, whether available.

    * Wildcard example: `http://example.com/1/3/6/1/2/1/118/1/1/2/a_name/*/1`

    * Wildcard example: `http://example.com/1/3/6/1/2/1/118/1/1/2/a_name/1342/*`

    * Wildcard (short) example: `http://example.com/1/3/6/1/2/1/118/1/1/2/a_name/1342/`

    * Wildcard example: `http://example.com/1/3/6/1/2/1/118/1/1/2/*/*/1`

  * **ORDERED_FILTER_URI = BASIC_URI + [`/ordered,list,of,tabular,fields`]**

    * Example: `http://example.com/1/3/6/1/2/1/118/1/1/2/4,7,6`

  * **UNORDERED_FILTERED_URI = BASIC_URI + [`/unordered;sequence;of;tabular;fields`]**

    * Example: `http://example.com/1/3/6/1/2/1/118/1/1/2/4;6;9`

  * **INDEXED_ORDERED_FILTER_URI = BASIC_URI + INDEXED_URI + ORDERED_FILTER_URI**

    * Example: `http://example.com/1/3/6/1/2/1/118/1/1/2/a_name/1342/1/5,7,6`

    * Wildcard example: `http://example.com/1/3/6/1/2/1/118/1/1/2/a_name/*/1/5,7,6`

  * **INDEXED_UNORDERED_FILTER_URI = BASIC_URI + INDEXED_URI + UNORDERED_FILTER_URI**

    * Example: `http://example.com/1/3/6/1/2/1/118/1/1/2/a_name/1342/1/4;6;9`

    * Wildcard example: `http://example.com/1/3/6/1/2/1/118/1/1/2/a_name/*/1/4;6;9`

Regarding a fully composed URI with any indexing or filtering usage, there is something important to highlight that may constrain clients (and servers) technical implementations. While the [HTTP 1.1 standard](https://tools.ietf.org/rfcmarkup?#section-3.2.1) states the following:

> The HTTP protocol does not place any a priori limit on the length of a URI. Servers MUST be able to handle the URI of any resource they serve and SHOULD be able to handle URIs of unbounded length if they provide GET-based forms that could generate such URIs. A server SHOULD return 414 (Request-URI Too Long) status if a URI is longer than the server can handle (see section 10.4.15). 

The actual situation is better clearly described in Sam Ruby and Leonard Richardson's _RESTful Web Services_:

> The HTTP standard doesn't impose any restrictions on URI length, but real web servers and clients do. For instance, Microsoft Internet Explorer can't handle URIs longer than 2,083 characters, and Apache won't respond to requests for URIs longer than 8 KBs. If some of your resources are only addressable given a great deal of scoping information, you may have to accept some of it in HTTP headers, or use overloaded POST and put scoping information in the entity-body. 

So, when speaking about URI length, it's important to think ahead about this length problem and consider the two possible alternative solutions.

Thank you for reading! In the next post, we'll go deeper by mapping SNMP operations.
